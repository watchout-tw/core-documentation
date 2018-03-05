# Committee

- [List committees](#list-committees)
- [Get a single committee](#get-a-single-committee)
- [Create a committee](#create-a-committee)
- [Update a committee](#update-a-committee)
- [Delete a committee](#delete-a-committee)

## List committees
```
GET /console/lab/committees
```

### Auth
- “editor”

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | 用姓名過濾委員會清單 | partial | `交通` `委員會` |

### Response
```
{
  rows: [
    {
      name
      abbreviation
      category
    }
    ...
  ]
  totalRowCount
}
```

## Get a single committee
```
GET /console/lab/committees/:name
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  name
  abbreviation
  category
}
```

## Create a committee
```
POST /console/lab/committees
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `name` | string | 🌕 | 名稱 |
| `abbreviation` | string | 🌕 | 簡稱 |
| `category` | string: directories.committee_category | 🌕 | 分類 |

### Sample input
```json
{
  "name": "交通委員會",
  "abbreviation": "交通",
  "category": "regular"
}
```

### Response
> Returns the newly created committee

## Update a committee
```
PATCH /console/lab/committees/:name
```

### Auth
- “editor”

### Paging
NO

> 參考 [Create a committee](#create-a-committee)

## Delete a committee
```
DELETE /console/lab/committees/:name
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
