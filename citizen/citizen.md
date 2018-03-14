# Citizen

## Get self
```
GET /citizen
```

### Auth
- “citizen” AND “self”

### Paging
NO

### Response
```
{
  id
  handle
  type
  status
  name
  gender
  birth_year
  birth_month
  birth_date
  country_code
  phone_number
  electorial_registration: {
    city
    district
    neighborhood
  }
  data: {}
  personas: [ // GET /personas
    *personaObject*
    ...
  ]
}
```

## Update self
```
PATCH /citizen
```

### Auth
- “citizen” AND “self”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `name` | string | 🌑 | 真實姓名 |
| `gender` | int | 🌑 | 性別認同 |
| `birth_year` | int | 🌑 | 出生年 |
| `birth_month` | int | 🌑 | 出生月 |
| `birth_date` | int | 🌑 | 出生日 |
| `country_code` | int | 🌑 | 電話號碼國碼 |
| `phone_number` | string | 🌑 | 電話號碼 |
| `electorial_registration` `[1]` | object | 🌑 | 選舉人資訊 |
| `data` | object | 🌑 | 其他資料 |

`[1]`
| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `city` | string | 🌑 | 城市 |
| `district` | string | 🌑 | 區域 |
| `neighborhood` | string | 🌑 | 里 |

### Sample input
```json
{
  "name": "黃培閎",
  "gender": 95,
  "birth_year": 1990,
  "birth_month": 9,
  "birth_date": 17,
  "country_code": 886,
  "phone_number": "912345678",
  "electorial_registration": {
    "city": "台北市",
    "district": "士林區",
    "neighborhood": "福林里"
  }
}
```

### Response
> Returns the updated citizen
