# Caucus

- [List Caucuses](#list-caucuses)
- [Get a single caucus](#get-a-single-caucus)
- [Create a caucus](#create-a-caucus)
- [Update a caucus](#update-a-caucus)
- [Delete a caucus](#delete-a-caucus)

## List Caucuses

```
GET /console/lab/caucuses
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | The name of the caucus. | partial | `無黨`,`無黨籍` |

### Response

``` js
{
  rows: [
    {
      name,
      abbreviation,
      type,
      emblem,
      color,
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
  emblem,
  color,
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
| `emblem` | string | The url path of the caucus's emblem. |
| `color` | string array | The symbolic color of the caucus. |
| `basic_info` | string | Basic information of the caucus. |
| `add_info` | string | Additional information of a caucus. |

### Example

``` json
{
  "name": "無黨籍",
  "abbreviation": "無黨籍",
  "emblem": "/path/to/emblem.png",
  "color": "#000,#fff",
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
  emblem,
  color,
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
| `emblem` | string | The url path of the caucus's emblem. |
| `color` | string array | The symbolic color of the caucus. |
| `basic_info` | string | Basic information of the caucus. |
| `add_info` | string | Additional information of a caucus. |

### Example

``` json
{
  "name": "無黨籍",
  "abbreviation": "無黨籍",
  "emblem": "/path/to/emblem.png",
  "color": "#000,#fff",
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
  emblem,
  color,
  basic_info,
  add_info
}
```

## Delete a Caucus

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
