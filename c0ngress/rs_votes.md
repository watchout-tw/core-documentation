# Vote (rep speech)

## Get a single vote
```
GET /c0ngress/rs_vote/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  id
  st_id
  date
  term_index
  session_index
  temp_session_index
  title
  content
  aye: [int ...]
  nay: [int ...]
  abstain: [int ...]
  absence: [int ...]
}
```
