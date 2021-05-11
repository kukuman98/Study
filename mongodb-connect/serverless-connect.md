# serverless connect

STEP1: Create db.py setup init\_db function to connect client server

```python
from typing import Dict

from mongoengine import connect
from pymongo import MongoClient, database

from api.settings import settings

DB_NAME: str = "service_xxx"
ROOT_DB_NAME: str = "service_root"
DB_ALIAS = f"{DB_NAME}_alias"
ROOT_DB_ALIAS: str = f"{ROOT_DB_NAME}_alias"

dbs: Dict[str, MongoClient] = {}


def init_db() -> None:
    if dbs.get("client", None) is None:
        dbs["client"] = connect(DB_NAME, host=settings.CLIENT_HOST, alias=DB_ALIAS)

        # for mongoengine orm, but should be the same underline MongoClient
        connect(ROOT_DB_NAME, host=settings.CLIENT_HOST, alias=ROOT_DB_ALIAS)
        
def get_client_meta_db() -> database.Database:
    return dbs["client"]["service_xxx"]
```

STEP2: setup init\_db function when starting up the server, in main.py

```python
.
.
from api.db import init_db


init_db()
app = FastAPI(...)
.
.
.
```

STEP3: Using revdb to setup DataBase connect

```python
from revdb import Model as BaseModel

from api.settings import settings


class Model(BaseModel):
    meta = {"abstract": True, "db_host": settings.DB_HOST}

```

STEP4: Use the Model to inherit other jstorage model

```python
import json
from typing import Any, Dict

from api.models import Model
from api.settings import settings


class XXX(Model):
    meta = {"abstract": True, "collection": "xxx", "db_host": settings.DB_HOST}

    def to_json(self) -> Dict[str, Any]:
        result = super().to_json()
        result = json.loads(result)
        if "_id" in result:
            del result["_id"]
        assert isinstance(result, dict)
        return result

```

STEP5: Connect your client collection in mirco server

```python
xxx_model = XXX.from_client(kwargs["client"])
xxx_model.objects.create(**kwargs)
```

STEP6: Create RootClient and Client model, using db\_alias to connect

```python
class RootClient(Model):
    client_id = StringField(required=True, unique=True)
    meta = {
        "db_alias": ROOT_DB_NAME,
        "collection": "v1",
    }
    
class Client(Model):
    client_id = StringField(required=True, unique=True)
    
    # Your server client field
    xxx = xxxxField(required=True, default="")

    meta = {
        "db_alias": DB_ALIAS,
        "collection": settings.VERSION,
    }
```

STEP7: Custom authorize personal credential by project

```python
from fastel.authorizers import ClientSecretAuth, JWBaseAuth

from api.models.client import Client, RootClient


class CustomJWTAuth(JWBaseAuth):
    client_model_class = Client


class CustomClientSecretAuth(ClientSecretAuth):
    client_model_class = Client
    root_client_class = RootClient

```

STEP8: Use that Custom Auth to verify project client id or user token

```python
router = APIRouter()
@router.post("/xxx")
def xxx(
    credential: Credential = Depends(CustomJWTAuth(force=True)),
) -> Dict[str, Any]:
    .
    .
    .
```

### Additional

You can Using pymongo to connect MongoDB

```python
from pymongo import MongoClient, database

dbs: Dict[str, MongoClient] = {}
dbs["cluster_name"] = connect(DB_NAME, host=settings.CLIENT_HOST, alias=DB_ALIAS)

def get_client_meta_db() -> database.Database:
    return dbs["cluster_name"]["db_name"]
```

Use case

```python
Meta = get_client_meta_db()["collect_name"]
```

And use the mongo action

```python
Meta.find({"client_id": client_id})
```

