# Rep

- [List reps](#list-reps)
- [Get a single rep](#get-a-single-rep)
- [Create a rep](#create-a-rep)
- [Update a rep](#update-a-rep)
- [Delete a rep](#delete-a-rep)

## List reps

```
GET /console/lab/reps
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌕 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `page` | integer | 頁次 | exact | `1` |
| `all` | - | 要求所有委員的名單 | - | - |
| `name` | string | 用姓名過濾委員名單 | partial | `陳`,`陳阿草` |
| `term` | integer | 用屆期過濾委員名單 | exact | `8` |
| `district` | string | 用選區名稱過濾委員名單  | exact | `全國不分區` |
| `party` | integer | 用政黨過濾委員名單 | exact | `1` |

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
            abbreviation,
            zone_name,
            index
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
GET /console/lab/reps/:id
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
  gender,
  highest_edu_degree,
  edu_record: [str, ...],
  experience: [str, ...],
  policy_proposal: [str, ...],
  contacts: [
    {
      seq_no,
      name,
      phone,
      fax,
      address,
      is_active
    }
    ...
  ],
  parties: [
    {
      term_index,
      party: {
        id,
        name
      },
      caucus: {
        id,
        name
      },
      start_date,
      officer_title,
      note
    }
    ...
  ],
  terms: [
    {
      term_index,
      change_date,
      change_type,
      district_name,
      duty,
      note
    }
    ...
  ],
  sessions: [
    {
      term_index,
      session_index,
      committee_name,
      is_convener
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
| name | string | 姓名 |
| birth_date | timestamp | 生日 |
| gender | integer: [-100, 100] | 性別；-100表示100%女性、+100表示100%男性 |
| highest_edu_degree | string: directories.edu_degree | 最高學歷 |
| edu_record | array of strings (JSON) | 學歷 |
| experience | array of strings (JSON) | 經歷 |
| policy_proposal | array of strings (JSON) | 政見 |
| contacts | array of objects | 聯絡方式 |
| parties | array of objects | 政黨歷史 |
| terms`[1]` | array of objects | 選任歷史 |
| sessions | array of objects | 委員會歷史 |

`[1]`

| Key | Type | Description |
| --- | --- | --- |
| term_index | integer | 屆期 |
| change_date | timestamp | 變更日期 |
| change_type | string: directories.rep_term_change_type | 變更類型 |
| district_name | string | 選區名稱 |
| duty | string: directories.rep_term_duty | 院內職務 |
| note | string | 備註 |

### Example

``` json
{
  "name": "陳阿草",
  "birth_date": 1501152358325,
  "gender": 0,
  "highest_edu_degree": "doctorate",
  "edu_record": [
    "Lorem ipsum.",
    "Lorem ipsum."
  ],
  "experience": [
    "Lorem ipsum.",
    "Lorem ipsum."
  ],
  "policy_proposal": [
    "Lorem ipsum.",
    "Lorem ipsum."
  ],
  "contacts": [
    {
      "seq_no": 1,
      "name": "國會辦公室",
      "phone": "+886-2-2345-6789",
      "fax": "+886-2-2345-6789",
      "address": "台北市青島東路1號",
      "is_active": true
    }
  ],
  "parties": [
    {
      "term_index": 8,
      "party": 2,
      "caucus": 2,
      "start_date": 1501152358325,
      "officer_title": "黨團總召",
      "note": "Lorem ipsum."
    }
  ],
  "terms": [
    {
      "term_index": 8,
      "change_date": 1501152358325,
      "change_type": "assume_office_through_regular_election",
      "district_name": "台北市第一選舉區",
      "duty": "speaker",
      "note": "Lorem ipsum."
    }
  ],
  "sessions": [
    {
      "term_index": 8,
      "session_index": 1,
      "committee_name": "修憲委員會",
      "is_convener": false
    }
  ]
}
```

### Response

``` js
{
}
```

## Update a rep

```
PATCH /console/lab/reps/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a rep](#create-a-rep)

## Delete a rep

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
