# Committee

- [List Committees](#list-committees)
- [Get a single committee](#get-a-single-committee)
- [Create a committee](#create-a-committee)
- [Update a committee](#update-a-committee)
- [Delete a committee](#delete-a-committee)

## List Committees

```
GET /console/lab/committees
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | The name of the committee. | partial | `交通`,`委員會` |

### Response

```
{
  rows: [
    {
      name,
      abbreviation,
      category
    }
  ],
  totalRowCount
}
```

## Get a single committee

```
GET /console/lab/committees/:name
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response

```
{
  name,
  abbreviation,
  category
}
```

## Create a committee

```
POST /console/lab/committees
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `name` | string | **Required.** The name of the committee. |
| `abbreviation` | string | **Required.** The abbreviation of the committee. |
| `category` | string | **Required.** The category of the committee. |

### Example

``` json
{
  "name": "交通委員會",
  "abbreviation": "交通",
  "category": "regular"
}
```

### Response

```
{
  name,
  abbreviation,
  category
}
```

## Update a committee

```
PATCH /console/lab/committees/:name
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `name` | string | The name of the committee. |
| `abbreviation` | string | The abbreviation of the committee. |
| `category` | string | The category of the committee. |

### Example

``` json
{
  "name": "交通委員會",
  "abbreviation": "交通",
  "category": "regular"
}
```

### Response

```
{
  name,
  abbreviation,
  category
}
```

## Delete a committee

```
DELETE /console/lab/committees/:name
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response

``` JSON
Status: 204 No Content
```
