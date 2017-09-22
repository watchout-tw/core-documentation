# Rep speech

## Get a single statement (rep speech)
```
GET /c0ngress/rs_statements/:id
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

## Get a single bill (rep speech)
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

## Get a single vote (rep speech)
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
