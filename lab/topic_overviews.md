# Topic Overview

- [List topic overviews](#list-topic-overviews)
- [Get a single topic overview](#get-a-single-topic-overview)

## List topic overviews
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
      slug
      image
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

## Get a single topic overview
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
  slug
  image
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
      image
      title
      st: {
        id
        name
      }
      figure_data_set_type
      figure_data_set
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
  related_links: [

  ]
}
```

> 以下與[`GET /lab/data_reports/:id`](./data_reports#get-a-single-data-report)格式保持一致
> type為`LAB_Bill_Data_Set`的data_set忽略`bills`及`scores`
> type為`LAB_Statement_Data_Set`的data_set忽略`should_have_spoken_*`及`statements`

```
figure_data_set_type: 'LAB_Bill_Data_Set'
figure_data_set: {
  id
  name
  version_no
  slug
  term_index
  start_date
  end_date
  st: {
    id
    name
  }
  act: {
    id
    title
  }
  act_dir: {
    id
    name
  }
  act_features: [
    {
      id
      feature
      dir
      content
      scale_score_max
      scale: [
        {
          score
          description
        }
        ...
      ]
    }
    ...
  ]
}
```

```
figure_data_set_type: 'LAB_Statement_Data_Set'
figure_data_set: {
  id
  name
  version_no
  slug
  term_index
  state_date
  end_date
  st: {
    id
    name
  }
  st_question: {
    id
    question
  }
  acts: [
    {
      id
      title
    }
    ...
  ]
}
```
