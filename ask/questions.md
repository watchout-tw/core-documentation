# Question of ASK

## List questions
```
GET /ask/questions
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
      game
      index
      topic_type
      topic_id
      image
      title
      content
      chatroom_id
      persona: {}
      references: [
        {}
        ...
      ]
      data: {}
      assigned_personas: [
        *personaObject*
        ...
      ]
      answers: [
        {
          id
          status
          slug
          index
          image
          content
          question
          persona
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
