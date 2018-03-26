# Question of ASK

## List questions
```
GET /ask/questions
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
      type
      persona: {}
      game: {}
      index
      topic_type
      topic_id
      image
      title
      content
      references: [
        {}
        ...
      ]
      chatroom_id
      data: {}
      assigned_personas: [ // [1]
        *personaObject*
        ...
      ]
      persona_speech_targets: [ // [2]
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
      persona_speeches: [ // [3]
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
      push: {
        count // [4]
      }
      answers: [
        {
          id
          status
          slug
          persona: {}
          index
          image
          content
          references: [
            {}
            ...
          ]
          data: {}
        }
      ]
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
> From ASK_Question_Assigned_Persona

`[2]`
> 以這個Q為source的Persona_Speech_Target列表

`[3]`
> **以目前active persona為發言人**，以`[1]`所列任一Persona_Speech_Target為target的Persona_Speech列表

`[4]`
> 計算以`[2]`所列target中任一為target，且type是ask_question_push的Persona_Speech數量，也就是這個Q的連署人數
