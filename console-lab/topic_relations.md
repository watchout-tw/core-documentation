# Topic Relation

- [List topic relations](#list-topic-relations)
- [Get a single topic relation](#get-a-single-topic-relation)
- [Create a topic relation](#create-a-topic-relation)
- [Update a topic relation](#update-a-topic-relation)
- [Delete a topic relation](#delete-a-topic-relation)

## List topic relations
```
GET /console/lab/topic_relations
```

### Auth
- “editor”

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `from_type` | string | type of from node | exact | `Specific_Topic` |
| `from_id` | integer | ID of from node | exact | `1` |
| `to_type` | string | type of to node | exact | `Act` |
| `to_id` | integer | ID of to node | exact | `2` |
| `search_directionally` | boolean | **[1]** | exact | `false` `true` |

**[1]**

> 當`search_directionally`為`false`，則

| `from_type` | `from_id` | `to_type` | `to_id` | `WHERE` |
| --- | --- | --- | --- | --- |
| `X` | - | - | - | `from_type IS X` OR `to_type IS X` |
| - | `1` | - | - | `from_id IS 1` OR `to_id IS 1` |
| `X` | `1` | - | - | EITHER ① `from_type IS X` AND `from_id IS 1` **OR** ② `to_type IS X` AND `to_id IS 1` |
| `X` | - | `Y` | - | EITHER ① `from_type IS X` AND `to_type IS Y` **OR** ② vice versa |
| `X` | `1` | `Y` | - | EITHER ① `from_type IS X` AND `from_id IS 1` AND `to_type IS Y` **OR** ② `from_type IS Y` AND `to_type IS X` AND `to_id IS 1` |
| `X` | `1` | `Y` | `2` | EITHER ① `from_type IS X` AND `from_id IS 1` AND `to_type IS Y` AND `to_type IS 2` **OR** ② `from_type IS Y` AND `from_id IS 2` AND `to_type IS X` AND `to_type IS 1` |

> 當`search_directionally`為`true`，則

| `from_type` | `from_id` | `to_type` | `to_id` | `WHERE` |
| --- | --- | --- | --- | --- |
| `X` | - | - | - | `from_type IS X` |
| - | `1` | - | - | `from_id IS 1` |
| `X` | `1` | - | - | `from_type IS X` AND `from_id IS 1` |
| `X` | - | `Y` | - | `from_type IS X` AND `to_type IS Y` |
| `X` | `1` | `Y` | - | `from_type IS X` AND `from_id IS 1` AND `to_type IS Y` |
| `X` | `1` | `Y` | `2` | `from_type IS X` AND `from_id IS 1` AND `to_type IS Y` AND `to_type IS 2` |

### Response
```
{
  rows: [
    {
      from_type
      from_id
      to_type
      to_id
      is_directional
      weight
      description
    }
    ...
  ]
  totalRowCount
}
```

## Get a single topic relation
```
GET /console/lab/topic_relations/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  from_type
  from_id
  to_type
  to_id
  is_directional
  weight
  description
}
```

## Create a topic relation
```
POST /console/lab/topic_relations
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Description |
| --- | --- | --- |
| `from_type` | string | 關係起點節點類型 |
| `from_id` | integer | 關係起點節點 ID |
| `to_type` | string | 關係終點節點類型 |
| `to_id` | integer | 關係終點節點 ID |
| `is_directional` | boolean | 關係是否為單向？ |
| `weight` | integer | 關係權重 |
| `description` | string | 關係敘述 |

### Sample input
```json
{
  "from_type": "Specific_Topic",
  "from_id": 1,
  "to_type": "Act",
  "to_id": 2,
  "is_directional": false,
  "weight": 42,
  "description": "Lorem ipsum."
}
```

### Response
> Returns the newly created topic_relation

## Update a topic relation
```
PATCH /console/lab/topic_relations/:id
```

### Auth
- “editor”

### Paging
NO

> 參考 [Create a topic relation](#create-a-topic-relation)

## Delete a topic relation
```
DELETE /console/lab/topic_relations/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
