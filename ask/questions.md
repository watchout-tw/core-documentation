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
      push_count // 這個問題的連署人數 [1]
      assigned_personas: [ // [2]
        *personaObject*
        ...
      ]
      persona_speech_target: {
        start_date
        end_date
        data: {}
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
}
```

`[1]`
> 計算target是這個Q的speech target，且type是ask_question_push的Persona_Speech

`[2]`
> ASK_Question_Assigned_Persona
