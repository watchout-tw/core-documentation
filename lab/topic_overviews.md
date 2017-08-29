# Topic Overview

- [List topic overviews](#list-topic-overviews)
- [Get a single topic overview](#get-a-single-topic-overview)

## List act features
```
GET /lab/topic_overviews
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  rows: [
    {
      id
      status
      st: {
        id
        title
      }
      tagline
      intro
      description
    }
    ...
  ]
  totalRowCount
}
```

## Get a single topic overviews
```
GET /lab/topic_overviews/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  id
  status
  st: {
    id
    title
  }
  tagline
  intro
  description
  timeline: {

  }
  data_reports: [
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
      }
    }
    ...
  ]
  insights: [
    {
      id
      status
      slug
      title
    }
  ]
  related_links: *JSON*
}
```
