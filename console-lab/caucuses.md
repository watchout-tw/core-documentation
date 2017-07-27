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

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | 用姓名過濾黨團清單 | partial | `無`,`國民` |

### Response

``` js
{
  rows: [
    {
      name,
      abbreviation,
      type,
      color,
      emblem,
      basic_info,
      add_info,
      status
    }
    ...
  ],
  totalRowCount
}
```

## Get a single caucus

```
GET /console/lab/caucuses/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response

``` js
{
  id,
  name,
  abbreviation,
  color,
  emblem,
  basic_info,
  add_info
}
```

## Create a caucus

```
POST /console/lab/caucuses
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `name` | string | **Required.** The name of the caucus. |
| `abbreviation` | string | **Required.** The abbreviation of the caucus. |
| `color` | string array | The symbolic color of the caucus. |
| `emblem` | string | The url path of the caucus's emblem. |
| `basic_info` | string | Basic information of the caucus. |
| `add_info` | string | Additional information of the caucus. |

### Example

``` json
{
  "name": "無黨籍",
  "abbreviation": "無黨籍",
  "color": "#000,#fff",
  "emblem": "/path/to/emblem.png",
  "basic_info": "Lorem Ipsum.",
  "add_info": "Lorem Ipsum."
}
```

### Response

``` js
{
  id,
  name,
  abbreviation,
  color,
  emblem,
  basic_info,
  add_info
}
```

## Update a caucus

```
PATCH /console/lab/caucuses/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `name` | string | The name of the caucus. |
| `abbreviation` | string | The abbreviation of the caucus. |
| `color` | string array | The symbolic color of the caucus. |
| `emblem` | string | The url path of the caucus's emblem. |
| `basic_info` | string | Basic information of the caucus. |
| `add_info` | string | Additional information of a caucus. |

### Example

``` json
{
  "name": "無黨籍",
  "abbreviation": "無黨籍",
  "color": "#000,#fff",
  "emblem": "/path/to/emblem.png",
  "basic_info": "Lorem Ipsum.",
  "add_info": "Lorem Ipsum."
}
```

### Response

``` js
{
  id,
  name,
  abbreviation,
  color,
  emblem,
  basic_info,
  add_info
}
```

## Delete a caucus

```
DELETE /console/lab/caucuses/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response

``` js
204 No Content
```
