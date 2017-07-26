# Rep

- [List reps](#list-reps)
- [Get a single rep](#get-a-single-rep)
- [Create a rep](#create-a-rep)
- [Update a rep](#update-a-rep)
- [Delete a rep](#delete-a-rep)

## List Reps

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌕 |

```
GET /console/lab/reps
```

### Parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | The name of the caucus. | partial | `無黨`,`無黨籍` |

### Response

```
Status: 200 OK

[
  {
    id,
    name,
    history: [
      {
        term,
        party: {
          id,
          name,
          color,
          emblem,
          abbreviation
        },
        district: {
          name,
          index,
          zone_name,
          abbreviation
        },
        change_type
      }
    ]
  },
  totalRowCount,
  paging: {
    pages,
    pageSize,
    previous,
    next,
    page
  }
]
```

## Get a single rep

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌕 |

```
GET /console/lab/reps/:id
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

## Create a caucus

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |


```
POST /console/lab/reps
```

### Input

| Key | Type | Description |
| --- | --- | --- |
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

## Update a party

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

```
PATCH /console/lab/reps/:id
```

### Input

| Key | Type | Description |
| --- | --- | --- |
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

## Delete a Caucus

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

```
DELETE /console/lab/reps/:id
```

### Response

``` js
Status: 204 No Content
```