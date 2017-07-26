# Caucus

- [List Caucuses](#list-caucuses)
- [Get a single caucus](#get-a-single-caucus)
- [Create a caucus](#create-a-caucus)
- [Update a caucus](#update-a-caucus)
- [Delete a caucus](#delete-a-caucus)

## List Caucuses

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

```
GET /console/lab/caucuses
```

### Parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | The name of the caucus. | partial | `無黨`,`無黨籍` |

### Response

``` js
Status: 200 OK

[
  {
    name,
    abbreviation,
    type,
    emblem,
    color,
    basic_info,
    add_info,
    status
  },
  totalRowCount
]
```

## Get a single caucus

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

```
GET /console/lab/caucuses/:id
```

### Response

``` js
Status: 200 OK

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

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |


```
POST /console/lab/caucuses
```

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
  "emblem": "/xxx/xxx/emblem.png",
  "color": "#EAEAEA,#OOOOOO",
  "basic_info": "something.....",
  "add_info": "something....."
}
```

### Response

``` js
Status: 200 OK

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

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

```
PATCH /console/lab/caucuses/:id
```

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
  "emblem": "/xxx/xxx/emblem.png",
  "color": "#EAEAEA,#OOOOOO",
  "basic_info": "something.....",
  "add_info": "something....."
}
```

### Response

``` js
Status: 200 OK

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

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

```
DELETE /console/lab/caucuses/:id
```

### Response

``` js
Status: 204 No Content
```