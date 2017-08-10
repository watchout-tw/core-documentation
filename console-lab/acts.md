# Act

- [List acts](#list-acts)
- [Get a single act](#get-a-single-act)
- [Create an act](#create-an-act)
- [Update an act](#update-an-act)
- [Delete an act](#delete-an-act)

## List acts
```
GET /console/lab/acts
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `title` | string | 用標題來過濾法案清單 | partial | `民` `集會` |
| `st` | integer: specific topic ID | 用關聯小議題來過濾法案清單 | exact | `1` `2` |

### Response
```
{
  rows: [
    {
      id,
      title,
      official_seq_no,
      specific_topics: [
        {
          id,
          title,
          index,
          image
        }
        ...
      ]
    }
    ...
  ],
  totalRowCount
}
```

## Get a single act
```
GET /console/lab/acts/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  id,
  title,
  official_seq_no,
  specific_topics: [
    {
      id,
      title,
      index,
      image
    }
    ...
  ]
}
```

## Create an act
```
POST /console/lab/acts
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `title` | string | 標題 |
| `official_seq_no` | string | 院總字號；用字串提高彈性 |
| `specific_topics` | array of integers: specific topic IDs | 關聯小議題 ID 列表 |

### Sample input
```json
{
  "title": "民法",
  "official_seq_no": "9487",
  "specific_topics": [
    1, 2, 4
  ]
}
```

### Response
> Returns the newly created act

## Update an act
```
PATCH /console/lab/acts/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create an act](#create-an-act)

## Delete an act
```
DELETE /console/lab/acts/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
