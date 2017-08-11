# Poll

## List polls
```
GET /park/polls
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  rows: [
    {
      id,
      slug,
      name,
      options: [
        {
          ?... /* NoSQL */
        }
        ...
      ]
    }
  ],
  totalRowCount
}
```

## Get a single poll
```
GET /park/polls/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌑 | 🌑 |

### Response
```
{
  id,
  slug,
  name,
  options: [
    {
      ?... /* NoSQL */
    }
    ...
  ],
  tally: [
    {
      content: [citizen_speech_content],
      count: [number of appearances of identical content]
    }
    ...
  ]
}
```
> tally是這個poll所有citizen_speech的統計結果，會計算citizen_speech各種不同的content累積出現的次數。
