# Committee

- [List Committees](#list-committees)
- [Get a single committee](#get-a-single-committee)
- [Create a committee](#create-a-committee)
- [Update a committee](#update-a-committee)
- [Delete a committee](#delete-a-committee)

## List Committees

| Auth | Paging |
| ----- | ----- |
| False | False |

```
GET /console/lab/committees
```

### Parameters

| Key | Type | Description | Match | Example
| ----- | ----- | ----- | ----- | ----- |
| `name` | string | The name of the committee. | partial | `交通`,`委員會` |

### Response

``` JSON
Status: 200 OK

[
  {
    name
    abbreviation,
    category
  },
  totalRowCount
]
```

## Get a single committee

| Auth | Paging |
| ----- | ----- |
| False | False |

```
GET /console/lab/committees/:name
```

### Response

``` JSON
Status: 200 OK

{
  name
  abbreviation,
  category
}
```

## Create a committee

| Auth | Paging |
| ----- | ----- |
| True | False |

```
POST /console/lab/committees
```

### Input

| Key | Type | Description |
| ----- | ----- | ----- | ----- |
| `name` | string | **Required.** The name of the committee. |
| `abbreviation` | string | **Required.** The abbreviation of the committee. |
| `category` | string | **Required.** The category of the committee. |

### Example

``` JSON
{
  "name": "交通委員會",
  "abbreviation": "交通",
  "category": "regular"
}
```

### Response

``` JSON
Status: 200 OK

{
  name
  abbreviation,
  category
}
```

## Update a committee

| Auth | Paging |
| ----- | ----- |
| True | False |

```
PATCH /console/lab/committees/:name
```

### Input

| Key | Type | Description |
| ----- | ----- | ----- | ----- |
| `name` | string | The name of the committee. |
| `abbreviation` | string | The abbreviation of the committee. |
| `category` | string | The category of the committee. |

### Example

``` JSON
{
  "name": "交通委員會",
  "abbreviation": "交通",
  "category": "regular"
}
```

### Response

``` JSON
Status: 200 OK

{
  name
  abbreviation,
  category
}
```

## Delete a committee

| Auth | Paging |
| ----- | ----- |
| True | False |

```
DELETE /console/lab/committees/:name
```

### Response

``` JSON
Status: 204 No Content
```