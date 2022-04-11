# Banners

- [List banners](#list-banners)
- [Get a single banner](#get-a-single-banner)
- [Create a banner](#create-a-banner)
- [Update a banner](#update-a-banner)
- [Update some banners](#update-some-banners)
- [Delete a banner](#delete-a-banner)

## List banners
```
GET /console/comp/banners
```

### Auth
- “editor”

### Paging
NO

### Available query parameters
NO

### Response
```
{
  rows: [
    {
      id
      index
      image
      url
    }
    ...
  ]
}
```

## Get a single banner
```
GET /console/comp/banners/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  id
  index
  image
  url
}
```

## Create a banner
```
POST /console/comp/banners
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `image` | string | 🌕 | 圖片網址 |
| `url` | string | 🌕 | 連結 |

### Sample input
```json
{
  "image": "https://i.waa.tw/68wfwe8fs",
  "url": "https://watchout.tw"
}
```

### Response
> Returns the newly created banner

### Notes
index 會自動設定為目前的最大值 + 1

## Update a banner
```
PATCH /console/comp/banners/:id
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `id` | integer | 🌕 | Banner ID |
| `index` | integer | 🌕 | 排序 |
| `image` | string | 🌕 | 圖片網址 |
| `url` | string | 🌕 | 連結 |

### Sample input
```json
{
  "id": 1,
  "index": 2,
  "image": "https://i.waa.tw/68wfwe8fs",
  "url": "https://watchout.tw"
}
```

## Update some banners
```
PATCH /console/comp/banners/
```

### Auth
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `items` | array of banner objects | 🌕 | 要修改的 Banners |

#### items

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `id` | integer | 🌕 | Banner ID |
| `index` | integer | 🌕 | 排序 |
| `image` | string | 🌕 | 圖片網址 |
| `url` | string | 🌕 | 連結 |

### Sample input
```json
{
  "items": [
    {
      "id": 1,
      "index": 2,
      "image": "https://i.waa.tw/68wfwe8fs",
      "url": "https://watchout.tw"
    },
    {
      "id": 2,
      "index": 3,
      "image": "https://i.waa.tw/68wfwe8fs",
      "url": "https://watchout.tw"
    }
  ]
}
```

## Delete a banner
```
DELETE /console/comp/banners/:id
```

### Auth
- “editor”

### Paging
NO

### Response
```javascript
204 No Content
```
