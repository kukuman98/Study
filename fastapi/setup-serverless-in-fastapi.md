# setup serverless in fastapi

STEP1: create domain in serverless

* config your npm scripts
* ```javascript
  "scripts": {
      ...
      "create_domain": "sls create_domain"
    }
  ```
* run the script command
* ```text
  npm run create_domain
  ```

STEP2: deploy the project to server

* config your npm scripts
* ```javascript
  "scripts": {
      ...
      "deploy:stg": "sls deploy -c serverless-stg.yml",
      "deploy:prod": "sls deploy -c serverless-prod.yml",
    }
  ```

STEP3: setup your serverless-stg.yml and serverless-prod.yml file

STEP4: try to run deploy

```bash
npm run deploy:stg/prod
```

STEP5: create your github action manual.yml file

```javascript
# This is a basic workflow that is manually triggered

name: Manual workflow

# Controls when the action will run. Workflow runs when manually triggered using the UI
# or API.
on:
  workflow_dispatch:
    # Inputs the workflow accepts.
    inputs:
      stage:
        # Friendly description to be shown in the UI instead of 'name'
        description: 'STAGE to deploy'
        # Default value if no value is explicitly provided
        default: 'stg'
        # Input has to be provided for the workflow to run
        required: true

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  # This workflow contains a single job called "greet"
  deploy-sls:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      - uses: actions/checkout@v2
        with:
          ref: master
          
      - uses: actions/setup-node@v2
        with:
          node-version: '14'
          
      - uses: actions/setup-python@v2
        with:
          python-version: "3.9"
          
      - name: Run image
        uses: abatilo/actions-poetry@v2.0.0
        with:
          poetry-version: "1.1.5"
      
    # Runs a single command using the runners shell
      - name: Deploy SLS
        run: |
          export AWS_ACCESS_KEY_ID=${{ secrets.AWS_ACCESS_KEY_ID }}
          export AWS_SECRET_ACCESS_KEY=${{ secrets.AWS_SECRET_ACCESS_KEY }}
          npm i
          npm run deploy:${{ github.event.inputs.stage }}

```

STEP6: Using github action to maintain project server version

