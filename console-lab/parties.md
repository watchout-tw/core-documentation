# Party

- [List parties](#list-parties)
- [Get a single party](#get-a-single-party)
- [Create a party](#create-a-party)
- [Update a party](#update-a-party)
- [Delete a party](#delete-a-party)

## List parties

```
GET /console/lab/parties
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | 用姓名過濾政黨清單 | partial | `無`,`民` |

### Response

``` js
{
  rows: [
    {
      id,
      name,
      abbreviation,
      color,
      emblem,
      basic_info,
      add_info
    }
    ...
  ],
  totalRowCount
}
```

## Get a single party

```
GET /console/lab/parties/:id
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

## Create a party

```
POST /console/lab/parties
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `name` | string | **Required.** The name of the party. |
| `abbreviation` | string | **Required.** The abbreviation of the party. |
| `color` | string array | The symbolic color of the party. |
| `emblem` | string | The url path of the party's emblem. |
| `basic_info` | string | Basic information of the party. |
| `add_info` | string | Additional information of a party. |

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

## Update a party

```
PATCH /console/lab/parties/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `name` | string | The name of the party. |
| `abbreviation` | string | The abbreviation of the party. |
| `color` | string array | The symbolic color of the party. |
| `emblem` | string | The url path of the party's emblem. |
| `basic_info` | string | Basic information of the party. |
| `add_info` | string | Additional information of the party. |

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

## Delete a party

```
DELETE /console/lab/parties/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response

``` js
204 No Content
```
