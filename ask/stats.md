# Stats of Game of ASK

- [Get review count](#get-review-count)
- [Get review average of each player](#get-review-average-of-each-player)
- [Get review average of each player at each topic](#get-review-average-of-each-player-at-each-topic)
- [Get number of answered question of each player](#get-number-of-answered-question-of-each-player)
- [Get popular questions of each player](#get-popular-questions-of-each-player)

## Get review count
```
GET /ask/games/:gameSlug/stats/review_count
```

### Auth

NO

### Paging

NO

### Response
```
{
  count: 9487
}
```

## Get review average of each player
```
GET /ask/game/:gameSlug/stats/player_review_average
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
      persona_id: 1
      score: 2.4
    }
    {
      persona_id: 2
      score: 4.2
    }
    ...
  ]
  totalRowCount
}
```

## Get review average of each player at each topic
```
GET /ask/game/:gameSlug/stats/player_topic_review_average
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
      persona_id: 1
      scores: [
        {
          topic_id: 1
          score: 2.4
        }
        {
          topic_id: 2
          score: 4.2
        }
        ...
      ]
    }
    ...
  ]
  totalRowCount
}
```

## Get number of answered question of each player
```
GET /ask/game/:gameSlug/stats/player_num_answered_questions
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
      persona_id: 1
      num_assigned_questions: 10
      num_answered_questions: 2
    }
    ...
  ]
  totalRowCount
}
```

## Get popular questions of each player
```
GET /ask/game/:gameSlug/stats/player_popular_questions
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
      persona: { // simplifiedPersonaObject
        id
        type
        status
        title
        name
        avatar
        start_date
        end_date
        data: {}
      }
      questions: [
        { // simplifiedQuestionObject
          id
          status
          slug
          type
          persona: {} // simplifiedPersonaObject
          topic_type
          topic_id  
          title
          content
          data: {} // threshold is here
          push: {
            count
          }
        }
        ...
      ]
    }
    ...
  ]
  totalRowCount
}
```
