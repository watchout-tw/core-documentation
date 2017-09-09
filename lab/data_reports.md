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
      principle_sponsor_parties: [

      ]
      sponsors: [

      ]
      cosponsors: [

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
  acts: [
    {
      id
      title
    }
    ...
  ]
  should_have_spoken_committees: [
    str, str, str
  ]
  should_have_spoken_sessions: [
    int, int, int
  ]
  statements: [
    {
      date
      term_index
      session_index
      temp_session_index
      rep
      rep_party
      principle_committee
      joint_committees: [
        str, str, str
      ]
      content
      position
      position_summary
      source_link
      tags: [
        int, int, int
      ]
    }
  ]
}
```