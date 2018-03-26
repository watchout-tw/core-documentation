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
          type
          content
          data: {}
        }
        ...
      ]
      review: {
        count // [3]
        average // [4]
      }
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
> 以這個A為source的Persona_Speech_Target列表

`[2]`
> **以目前active persona為發言人**，以`[1]`所列任一Persona_Speech_Target為target的Persona_Speech列表

`[3]`
> 所有以`[1]`所列target中任一為target，且type為ask_answer_review的Persona_Speech數目

`[4]`
> `[3]`所列的Persona_Speech取content平均值，也就是這個A的平均評分
