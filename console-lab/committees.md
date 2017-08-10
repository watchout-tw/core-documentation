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

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | 用姓名過濾委員會清單 | partial | `交通` `委員會` |

### Response
```
{
  rows: [
    {
      name,
      abbreviation,
      category
    }
    ...
  ],
  totalRowCount
}
```

## Get a single committee
```
GET /console/lab/committees/:name
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  name,
  abbreviation,
  category
}
```

## Create a committee
```
POST /console/lab/committees
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `name` | string | **Required.** 名稱 |
| `abbreviation` | string | **Required.** 簡稱 |
| `category` | string: directories.committee_category | **Required.** 分類 |

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

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a committee](#create-a-committee)

## Delete a committee
```
DELETE /console/lab/committees/:name
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
