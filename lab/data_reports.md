# Data Report

- [List data reports](#list-data-reports)
- [Get a single data report](#get-a-single-data-report)

## List data reports
```
GET /lab/data_reports
```

### Auth
NO

### Paging
NO

### Response
```
{
  rows: [
    {
      id
      status
      slug
      type
      image
      title
      st: {
        id
        title
      }
      figure_data_set_type
      figure_data_set
    }
    ...
  ]
  totalRowCount
}
```

> 如果`figure_data_set_type`是`LAB_Bill_Data_Set`的話⋯

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
    title
    image
    index
  }
  act: {
    id
    title
    official_seq_no
  }
  act_dir: {
    id
    name
  }
}
```

> 如果`figure_data_set_type`是`LAB_Statement_Data_Set`的話⋯

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
    title
  }
  st_question: {
    id
    question
  }
}
```

## Get a single data report
```
GET /lab/data_reports/:id
```

### Auth
NO

### Paging
NO

### Response
```
{
  id
  status
  slug
  type
  image
  title
  st: {
    id
    title
  }
  figure_data_set_type
  figure_data_set
  figures: [
    {
      id
      status
      slug
      type
      image
      title
      description
      summary
    }
    ...
  ]
}
```

> 與[`GET /lab/data_reports`](#list-data-reports)格式保持一致
> - type為`LAB_Bill_Data_Set`的data_set增加`act_features`、`bills`及`scores`
> - type為`LAB_Statement_Data_Set`的data_set增加`acts`、`should_have_spoken_*`及`statements`

> `rep_info_list`是`principle_sponsor_value`、`sponsors`、`cosponsors`之中所有不重複委員在該提案當下的政黨、黨團資訊。array中每個object與[`/c0ngress/date_to_rep_info`](../c0ngress/utilities#date-to-rep-info)格式保持一致

> 如果`figure_data_set_type`是`LAB_Bill_Data_Set`的話⋯

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
    title
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
  bills: [
    {
      id
      is_law
      date
      term_index
      session_index
      temp_session_index
      version_no
      principle_sponsor_type
      principle_sponsor_value
      principle_sponsor_parties: [int ...]
      sponsors: [int ...]
      cosponsors: [int ...]
      rep_info_list: [
        {
          id
          name
          party_id
          caucus_id
          committees: [
            {
              name
              is_convener
            }
            ...
          ]
        }
        ...
      ]
      content
      data_source_link
      progress_source_link
      tags
      legislative_steps: [
        {
          date
          legislative_step: {
            id
            name
          }
        }
        ...
      ]
      st_questions: [
        {
          st_question: {
            id
            question
          }
          position
        }
        ...
      ]
      act_features: [
        {
          act_dir: {
            id
            name
          }
          act_feature: {
            id
            feature
            dir
            content
          }
          short_content
          content
        }
        ...
      ]
    }
    ...
  ]
  scores: *JSON*
}
```

> 如果`figure_data_set_type`是`LAB_Statement_Data_Set`的話⋯

```
figure_data_set_type: 'LAB_Statement_Data_Set'
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
    title
  }
  st_question: {
    id
    question
  }
  should_have_spoken_committees: [str ...]
  should_have_spoken_sessions: [int ...]
  statements: [
    {
      date
      term_index
      session_index
      temp_session_index
      rep
      rep_party
      principle_committee
      joint_committees: [str ...]
      content
      position
      position_summary
      source_link
      tags: [int ...]
    }
  ]
}
```
