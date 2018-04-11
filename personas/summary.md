# Public info of a persona

## Public system summary of a persona
```
GET /personas/:id/summary
```

### Auth
NO

### Paging
NO

### Response
```
{
  ask_games: [
    {
      id
      status
      slug
      year
      type
      battlefield
      title
      before_title
      after_title
      image
      index
      data: {}
      players: []
      summary: {
        question_count
        answer_count
      }
      persona_summary: { // [1]
        num_questions_posted
        num_questions_posted_with_answer
        num_questions_pushed
        num_questions_assigned
        num_questions_answered
        num_answers_posted
        num_answers_reviewed
      }
    }
    ...
  ]
}
```

`[1]`

| Key | Type | Description |
| --- | --- | --- |
| `num_questions_posted` | integer | active persona已提出幾個問題？ |
| `num_questions_posted_with_answer` | integer | active persona所提問題中，有幾個問題已被回答？ |
| `num_questions_pushed` | integer | active persona已連署了幾個問題？ |
| `num_questions_assigned` | integer | 有多少問題已指定active persona回答？ |
| `num_questions_answered` | integer | active persona已回答了幾個問題？ |
| `num_answers_posted` | integer | active persona已提出了幾個答案？ |
| `num_answers_reviewed` | integer | active persona已評分了幾個答案？ |
