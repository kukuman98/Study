# Fetch Array Object

example data

```json
[
    {
        "id": "xxx1",
        "tool_id": "toolxxx1",
        "tools": [
            {
                "tool_id": "toolxxx1",
                "misc_data": "xxx1",
                ...
            },...
        ]
    },
    {
        "id": "xxx2",
        "tool_id": "toolxxx2",
        "tools": [
            {
                "tool_id": "toolxxx1",
                "misc_data": "xxx1",
                ...
            },...
        ]
    },...
]
```

case with $indexOfArray & $arrayElemAt

```python
conn.aggregate(
    [
        {"$match": {"id": {"$in": ["xxx1", "xxx2"]}},
        # 使用 $indexOfArray 找出 array 對應的 tool_id 所屬的 index
        {
            "$addFields": {
                "tool_index": {
                    "$indexOfArray": ["$tools.tool_id", "$tool_id"]
                }
            }
        },
        # 使用 #arrayElemAt 去取得 array 對應的 index object
        {
            "$addFields": {
                "tool": {
                    "$cond": {
                        "if": {"$in": ["$tool_id", "$tools.tool_id"]},
                        "then": {
                            "$arrayElemAt": [
                                "$tools",
                                "$tool_index",
                            ]
                        },
                        "else": {},
                    }
                },
            }
        },
        {
            "$unset": ["tools"]
        }
    ]
)
```

pymongo aggregate response

```json
[
    {
        "id": "xxx1",
        "tool_id": "toolxxx1",
        "tool": {
            "tool_id": "toolxxx1",
            "misc_data": "xxx1",
            ...
        },...
    },
    {
        "id": "xxx2",
        "tool_id": "toolxxx2",
        "tool": {
            "tool_id": "toolxxx2",
            "misc_data": "xxx2",
            ...
        },...
    },...
]
```
