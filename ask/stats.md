# Stats of Game in ASK

- [Get review count](#get-review-count)
- [Get review average of each guest](#get-review-average-of-each-guest)
- [Get review average grouped by topic of each guest](#get-review-average-grouped-by-topic-of-each-guest)
- [Get number of answered question of each guest](#get-number-of-answered-question-of-each-guest)

## Get review count
```
GET /ask/games/:slug/stats/review_count
```

### Auth
NO

### Paging
NO

### Response
{
  count: 5432
}

## Get review average of each guest
```
GET /ask/game/:slug/stats/guest_review_average
```

### Auth
NO

### Paging
NO

### Response
{
  rows: [
    { id: 1, score: 3.8 },
    { id: 2, score: 4.2 },
    ...
  ],
  totalRowCount: 4
}

## Get review average grouped by topic of each guest
```
GET /ask/game/:slug/stats/guest_topic_review_average
```

### Auth
NO

### Paging
NO

### Response
{
  rows: [
    {
      id: 1,
      scores: [
        { topic: 1, score: 4.8 },
        { topic: 2, score: 4 },
        ...
      ]
    },
    ...
  ],
  totalRowCount: 4
}

## Get number of answered question of each guest
```
GET /ask/game/:slug/stats/guest_answered_questions
```

### Auth
NO

### Paging
NO

### Response
{
  rows: [
    { id: 1, num_assigned_questions: 10, num_answered_questions: 2 },
    ...
  ],
  totalRowCount: 4
}
