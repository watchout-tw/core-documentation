# Data Report

- [Get a single data report](#get-a-single-data-report)

## Get a single topic overviews
```
GET /lab/data_reports/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  id
  status
  slug
  type
  title
  figure_data_set_type
  figure_data_set: {
    id
    name
    version_no
    term_index
    start_date
    end_date
    act_dir: {
      id
      name
    }
    act: {
      id
      title
    }
    data: *JSON*
  } *OR* {
    id
    name
    version_no
    term_index
    state_date
    end_date
    st_question: {
      id
      question
    }
    data: *JSON*
  }
  figures: [
    {
      id
      status
      slug
      type
      title
      description
      summary
    }
    ...
  ]
}
```
