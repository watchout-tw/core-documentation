# Figures

- [List figures](#list-figures)
- [Get a single figure](#get-a-single-figure)
- [Create a figure](#create-a-figure)
- [Update a figure](#update-a-figure)
- [Delete a figure](#delete-a-figure)

## List figures
```
GET /console/lab/figures
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `title` | string | 用標題過濾圖表 | partial | `法` `法條` |

### Response
```
{
  rows: [
    {
      id,
      status,
      type,
      title
    }
    ...
  ],
  totalRowCount
}
```

## Get a single figure
```
GET /console/lab/figure/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  id,
  status,
  slug,
  image,
  title,
  description,
  summary,
  data_set_type,
  data_set_id
}
```

## Create a figure
```
POST /console/lab/figure
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `status` | string | 狀態 |
| `slug` | string | 短網址 |
| `type` | string | 類型 |
| `image` | string | 圖像的路徑 |
| `title` | string | 標題 |
| `description` | string | 敘述 |
| `summary` | string | 摘要 |
| `data_set_type` | string | 資料集型別 |
| `data_set_id` | integer | 資料集 ID |

### Sample input
```json
{
  "status": "active",
  "slug": "bill-comp/recall/xxxx",
  "type": "基本",
  "image": "path/image.png",
  "title": "法條比一比",
  "description": "在提案連署過程中…",
  "summary": "能否讓罷免順利成功…",
  "data_set_type": "LAB_BILL_DATA_SET",
  "data_set_id": "1",
}
```

### Response
> Returns the newly created figure

## Update a figure
```
PATCH /console/lab/figure/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a figure](#create-a-figure)

## Delete a figure
```
DELETE /console/lab/figure/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
