# Answer of ASK

## List answers
```
GET /ask/answers
```

### Auth
NO

### Paging
YES

### Response
```
{
  rows: [
    {
      id
      status
      slug
      persona: {}
      question: {}
      index
      image
      content
      references: []
      data: {}
      persona_speech_targets: [ // [1]
        {
          id
          type
          source_entity
          source_id
          sp_type
          sp_per_persona
          start_date
          end_date
          data: {}
        }
        ...
      ]
      persona_speeches: [ // [2]
        {
          id
          target_id
          date
          time
          content
          data: {}
        }
        ...
      ]
      review_average
    }
    ...
  ]
  totalRowCount
  paging: {
    page
    pages
    pageSize
    previous
    next
  }
}
```

`[1]`
> 以這個A為source_entity的Persona_Speech_Target列表

`[2]`
> **以目前active persona為發言人**，以上列任一Persona_Speech_Target為target的Persona_Speech列表
