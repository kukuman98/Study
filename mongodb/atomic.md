# Atomic

Case with $cond:

```python
# 在 find_one_and_update 和 find_and_modify 的使用方式，
# update 可以是單獨的update document 也可以是 aggregate pipeline
# 支援在 MongoDB 4.2 版本
from pymongo import MongoClient
conn = MongoClient(xxx).get_database(xxx).get_collection(xxx)
conn.find_one_and_update(
    {
        "id": 0
    },
    [
        {
            "$set": {
                "count": {
                    "$cond": {
                        "if": {
                            "$gt": ["$count", 0]
                        },
                        "then": {
                            "$sum": ["$count", -1]
                        },
                        "else": 0
                    }
                }
            }
        }
    ]
)

```

Case with $switch

```python
conn.find_one_and_update(
    {
        "id": 0
    },
    [
        {
            "$set": {
                "count": {
                    "$switch": {
                        "branches": [
                            {
                                "case":{
                                    "$gt": ["$count", 0]
                                },
                                "then":{
                                    "$sum": ["$count", -1]
                                }
                            },
                            {
                                "case":{
                                    "$eq": ["$count", -1]
                                },
                                "then": -1
                            }
                        ],
                    "default": 0
                    }
                }
            }
        }
    ]
)
```
