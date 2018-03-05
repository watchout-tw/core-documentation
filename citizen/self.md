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
}
```
> persona清單在login response裡

## Update self
```
PATCH /citizen
```

### Auth
- “citizen” AND “self”

### Paging
NO
