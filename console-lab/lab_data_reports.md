# Data Reports

- [List data reports](#list-data-reports)
- [Get a single data report](#get-a-single-data-report)
- [Create a data report](#create-a-data-report)
- [Update a data report](#update-a-data-report)
- [Delete a data report](#delete-a-data-report)

## List data reports
```
GET /console/lab/data_reports
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `st` | integer: specific topic ID | 用關聯小議題過濾數據分析報告 | exact | `1` `2` |

### Response
```
{
  rows: [
    {
      id
      status
      slug
      type
      image
      title
      st: {
        id
        title
        image
        index
      }
      figure_data_set_type
      figure_data_set
      figures: [
        {
          id
          status
          slug
          type
          image
          title
        }
      ]
    }
    ...
  ]
  totalRowCount
}
```

> 如果`figure_data_set_type`是`LAB_Bill_Data_Set`的話⋯

```
figure_data_set: {
  id
  name
  version_no
  slug
  term_index
  start_date
  end_date
  st: {
    id
    title
  }
  act: {
    id
    title
  }
  act_dir: {
    id
    name
  }
}
```

> 如果`figure_data_set_type`是`LAB_Statement_Data_Set`的話⋯

```
figure_data_set: {
  id
  name
  version_no
  slug
  term_index
  state_date
  end_date
  st: {
    id
    title
  }
  st_question: {
    id
    question
  }
}
```

## Get a single data report
```
GET /console/lab/data_report/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  id
  status
  slug
  type
  image
  title
  st_id
  figure_data_set_type
  figure_data_set_id
  figures: [
    {
      id
      index
    }
    ...
  ]
}
```

## Create a data report
```
POST /console/lab/data_report
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `status` | string | 狀態 |
| `slug` | string | 短網址 |
| `type` | string | 類別 |
| `image` | string | 圖像的路徑 |
| `title` | integer | 標題 |
| `st_id` | integer | 關聯小議題 ID |
| `figure_data_set_type` | string | 資料源類型 |
| `figure_data_set_id` | integer | 資料源 ID |

### Sample input
```json
{
  "status": "active",
  "slug": "a/b/c",
  "type": "type",
  "image": "path/image.png",
  "title": "數據分析報告",
  "st_id": 1,
  "figure_data_set_type": "LAB_Bill_Data_Set",
  "figure_data_set_id": 2,
  "figures": [
    {
      "id": 1,
      "index": 1
    },
    {
      "id": 2,
      "index": 2
    }
  ]
}
```

### Response
> Returns the newly created data report

## Update a data report
```
PATCH /console/lab/data_report/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a data report](#create-a-data-report)

## Delete a data report
```
DELETE /console/lab/data_report/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
