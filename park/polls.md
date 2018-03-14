# Poll

## List polls
```
GET /park/polls
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
      slug
      name
      options: [
        {
          ?... /* NoSQL */
        }
        ...
      ]
    }
  ]
  totalRowCount
}
```

## Get a single poll
```
GET /park/polls/:id
```

### Auth
NO

### Paging
NO

### Response
```
{
  id
  slug
  name
  options: [
    {
      ?... /* NoSQL */
    }
    ...
  ]
  tally: [
    {
      content: [persona_speech_content]
      count: [number of appearances of identical content]
    }
    ...
  ]
}
```
> tally是這個poll所有persona_speech的統計結果，會計算persona_speech各種不同的content累積出現的次數。
