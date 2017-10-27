# Topic Overview

- [List data report figures](#list-data-report-figures)
- [Create a data report figure](#create-a-data-report-figure)
- [Update a data report figure](#update-a-data-report-figure)
- [Delete a data report figure](#delete-a-data-report-figure)

## List data report figures
```
GET /console/lab/data_report_figures
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `data_report` | integer: specific data report ID | 某個數據分析報告 | exact | `1` `2` |
| `figure` | integer: specific figure ID | 與數據分析報告關聯的圖表 | exact | `1` `2` |
| `index` | integer: specific index ID | 數據分析報告關聯圖表的排序 | exact | `1` `2` |

### Response
```
{
  rows: [
    {
      data_report_id
      figure_id
      index
    }
    ...
  ]
  totalRowCount
}
```

## Create a data report figure
```
POST /console/lab/data_report_figures
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `data_report_id` | integer | 🌕 |數據分析報告 ID |
| `figure_id` | integer | 🌕 | 圖表 ID |
| `index` | integer | 🌕 | 圖表的排序 |


### Sample input
```json
{
  "data_report_id": 1,
  "figure_id": 2,
  "index": 2
}
```

### Response
> Returns the newly created data report figure


## Delete a data report figure
```
DELETE /console/lab/data_report_figures/data_report/{data_report_id}/figure/{figure_id}/index/{index}
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
