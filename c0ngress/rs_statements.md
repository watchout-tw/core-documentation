# Statement (rep speech)

## Get a single statement
```
GET /c0ngress/rs_statements/:id
```

### Auth
NO

### Paging
NO

### Response
```
{
  id
  st_id
  date
  term_index
  session_index
  temp_session_index
  rep_id
  rep_party_id
  principle_committee
  joint_committees: [str ...]
  content
  st_question_id
  position
  position_summary
}
```
