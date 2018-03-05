# Caucus

- [List caucuses](#list-caucuses)
- [Get a single caucus](#get-a-single-caucus)
- [Create a caucus](#create-a-caucus)
- [Update a caucus](#update-a-caucus)
- [Delete a caucus](#delete-a-caucus)

## List caucuses
```
GET /console/lab/caucuses
```

### Auth
- “editor”

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | 用姓名過濾黨團清單 | partial | `無` `國民` |

### Response
```
{
  rows: [
    {
      id
      name
      abbreviation
      color
      emblem
      basic_info
      add_info
      type
      status
    }
    ...
  ]
  totalRowCount
}
```

## Get a single caucus
```
GET /console/lab/caucuses/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  id
  name
  abbreviation
  color
  emblem
  basic_info
  add_info
  type
  status
}
```

## Create a caucus
```
POST /console/lab/caucuses
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
| `color` | string array | 🌑 | 代表色 |
| `emblem` | string | 🌑 | 代表徽章的檔案路徑 |
| `basic_info` | string | 🌑 | 基本資訊 |
| `add_info` | string | 🌑 | 補充資訊 |
| `type` | string | 🌑 | 黨團/政團 |
| `status` | string | 🌑 | active/inactive… |

### Sample input
```json
{
  "name": "無黨籍",
  "abbreviation": "無黨籍",
  "color": "#000,#fff",
  "emblem": "/path/to/emblem.png",
  "basic_info": "Lorem ipsum.",
  "add_info": "Lorem ipsum.",
  "type": "政團",
  "status": "active"
}
```

### Response
> Returns the newly created caucus

## Update a caucus
```
PATCH /console/lab/caucuses/:id
```

### Auth
- “editor”

### Paging
NO

> 參考 [Create a caucus](#create-a-caucus)

## Delete a caucus
```
DELETE /console/lab/caucuses/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
