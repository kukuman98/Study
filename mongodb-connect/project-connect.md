# project connect

STEP1: Your can use revdb to connect project collection

```python
import json
from typing import Any, Dict

from revdb import collection_factory

from api.settings import settings

DataBase = collection_factory(
    client_secret=settings.CLIENT_SECRET,
    client_id=settings.CLIENT_ID,
    stage=settings.STAGE,
)
```

STEP2: Use the DataBase to connect other collection

```python
from api.models import DataBase

XXX = DataBase(collection="xxx")

```

STEP3: Use the collection to progress collection action

```python
def test():
    XXX.objects.create(...)
```

