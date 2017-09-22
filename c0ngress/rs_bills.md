# Bill (rep speech)

## Get a single bill
```
GET /c0ngress/rs_bill/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  id
  act_id
  is_law
  version_no
  date
  term_index
  session_index
  temp_session_index
  principle_sponsor_type
  principle_sponsor_value
  sponsors: [int ...]
  cosponsors: [int ...]
  content
}
```
