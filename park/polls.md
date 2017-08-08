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
  ]
}
```
