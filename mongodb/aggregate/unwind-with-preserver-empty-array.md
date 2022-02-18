# Unwind with preserver Empty array

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
        "tools": []
    },...
]
```

case with $unwind & preserveNullAndEmptyArrays

```python
conn.aggregate(
    [
        {"$match": {"id": {"$in": ["xxx1", "xxx2"]}},
        {
            "$unwind": {
                "path": "$tools",
                "preserveNullAndEmptyArrays": True
            }
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
        "tools": {
            "tool_id": "toolxxx1",
            "misc_data": "xxx1",
            ...
        },...
    },
    {
        "id": "xxx1",
        "tool_id": "toolxxx1",
        "tool": {
            "tool_id": "toolxxx3",
            "misc_data": "xxx3",
            ...
        },...
    },...
    {
        "id": "xxx2",
        "tool_id": "toolxxx2",
        "tool": null,
        ...
    }
]
```
