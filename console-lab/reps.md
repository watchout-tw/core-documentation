# Rep

- [List reps](#list-reps)
- [Get a single rep](#get-a-single-rep)
- [Create a rep](#create-a-rep)
- [Update a rep](#update-a-rep)
- [Delete a rep](#delete-a-rep)

## List Reps

```
GET /console/lab/reps
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌕 |

### Parameters

| Key | Type | Description | Match | Example |
| --- | :---: | --- | :---: | --- |
| `page` | integer | page number | exact | `1` |
| `all` | -- | get all data without paging | -- | `無黨`,`無黨籍` |
| `name` | string | The name of the rep. | partial | `阿草` |
| `term` | integer | To show rep's history data by whitch term | exact | `8` |
| `district` | string | To show rep's history data by whitch district  | exact | `全國不分區` |
| `party` | integer | To show rep's history data by whitch party | exact | `1` |

### Response

``` js
{
  rows: [
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
        ...
      ]
    }
    ...
  ],
  totalRowCount,
  paging: {
      pages,
      pageSize,
      previous,
      next,
      page
    }
}
```

## Get a single rep

```
GET /console/lab/rpes/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response

``` js
{
  id,
  name,
  birth_date,
  highest_edu_degree,
  edu_record: [str, ...],
  experience: [str, ...],
  policy_proposal,
  contacts,
  parties: [
    {
      note,
      party: {
        id,
        name
      },
      caucus: {
        id,
        name
      },
      start_date,
      term_index,
      officer_title
    },
  ],
  terms: [
    {
      duty,
      note,
      term_index,
      change_date,
      change_type,
      district_name,
    }
    ...
  ],
  sessions: [
    {
      term_index,
      is_convener,
      session_index,
      committee_name
    }
    ...
  ]
}
```

## Create a rep

```
POST /console/lab/reps
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
PATCH /console/lab/reps/:id
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

## Delete a Rep

```
DELETE /console/lab/reps/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response

``` js
204 No Content
```
