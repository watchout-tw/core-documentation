# Party

- [List Parties](#list-parties)
- [Get a single party](#get-a-single-party)
- [Create a party](#create-a-party)
- [Update a party](#update-a-party)
- [Delete a party](#delete-a-party)

## List Committees

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

```
GET /console/lab/parties
```

### Parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | The name of the party. | partial | `無黨`,`無黨籍` |


### Response

``` js
Status: 200 OK

[
  {
    name,
    abbreviation,
    emblem,
    color,
    basic_info,
    add_info
  },
  totalRowCount
]
```

## Get a single party

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

```
GET /console/lab/parties/:id
```

### Response

``` js
Status: 200 OK

{
  name,
  abbreviation,
  emblem,
  color,
  basic_info,
  add_info
}
```

## Create a party

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

```
POST /console/lab/parties
```

### Input

| Key | Type | Description |
| --- | --- | --- | --- |
| `name` | string | **Required.** The name of the party. |
| `abbreviation` | string | **Required.** The abbreviation of the party. |
| `emblem` | string | The url path of the party's emblem. |
| `color` | string array | The symbolic color of the party. |
| `basic_info` | string | Basic information of the party. |
| `add_info` | string | Additional information of a party. |


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

``` json
Status: 200 OK

{
  id,
  name
  abbreviation,
  emblem,
  color,
  basic_info,
  add_info
}
```

## Update a party

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

```
PATCH /console/lab/parties/:id
```

### Input

| Key | Type | Description |
| --- | --- | --- | --- |
| `name` | string | The name of the party. |
| `abbreviation` | string | The abbreviation of the party. |
| `emblem` | string | The url path of the party's emblem. |
| `color` | string array | The symbolic color of the party. |
| `basic_info` | string | Basic information of the party. |
| `add_info` | string | Additional information of a party. |

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

## Delete a party

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

```
DELETE /console/lab/parties/:id
```

### Response

``` JSON
Status: 204 No Content
```