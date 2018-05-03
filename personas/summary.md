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
        answer_review_average
      }
    }
    ...
  ]
}
```

`[1]`

| Key | Type | Description |
| --- | --- | --- |
| `num_questions_posted` | integer | active persona 已提出幾個問題？ |
| `num_questions_posted_with_answer` | integer | active persona 所提問題中，有幾個問題已被回答？ |
| `num_questions_pushed` | integer | active persona 已連署了幾個問題？ |
| `num_questions_assigned` | integer | 有多少問題已指定 active persona 回答？ |
| `num_questions_answered` | integer | active persona 已回答了幾個問題？ |
| `num_answers_posted` | integer | active persona 已提出了幾個答案？ |
| `num_answers_reviewed` | integer | active persona 已評分了幾個答案？ |
| `answer_review_average` | decimal | active persona 回答的所有問題的平均分數？ |
