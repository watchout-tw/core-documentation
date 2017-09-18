# Data Reports

- [List data reports](#list-data-reports)
- [Get a single act feature](#get-a-single-data-report)
- [Create a data reports](#create-a-data-report)
- [Update a data reports](#update-a-data-report)
- [Delete a data reports](#delete-a-data-report)

## List data reports
```
GET /console/lab/lab_data_reports
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `st` | integer: specific topic ID | 用關聯小議題過濾議題綜覽 | exact | `1` `2` |
| `timeline` | integer: timeline ID | 用大事紀過濾議題綜覽 | exact | `1` `2` |

### Response
```
{
  rows: [
    {
      id,
      status,
      st: {
        id,
        title,
        image,
        index
      },
      figure_data_set: {
        id,
        figure_data_set_type,
        name,
        version_no
      },
      figure: {
        id,
        type,
        title
      }
    }
    ...
  ],
  totalRowCount
}
```

## Get a single data report
```
GET /console/lab/lab_data_report/:id
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
  type,
  image,
  title,
  st_id,
  figure_data_set_type,
  figure_data_set_id
}
```

## Create a data report
```
POST /console/lab/lab_data_report
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
| `st_id` | integer | 關聯小議題 ID |
| `image` | string | 圖像的路徑 |
| `title` | integer | 標題 |
| `figure_data_set_type` | string | 資料源類型 |
| `figure_data_set_id` | integer | 資料源 ID |

### Sample input
```json
{
  "status": "active",
  "slug": "bill-comp/recall/xxxx",
  "type": "bill_comparison",
  "st_id": 1,
  "image": "path/image.png",
  "title": "數據分析報告",
  "figure_data_set_type": "LAB_Bill_Data_Set",
  "figure_data_set_id": 2
}
```

### Response
> Returns the newly created data report

## Update a data report
```
PATCH /console/lab/lab_data_report/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a data report](#create-a-data-report)

## Delete a data report
```
DELETE /console/lab/lab_data_report/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
