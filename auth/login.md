# Login
```
POST /auth/login
```

### Auth
NO

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `handle` | string | 🌕 `[1]` | 草民代號 |
| `email` | string | 🌕 `[1]` | Email |
| `password` | string | 🌕 | 密碼 |

`[1]`
> `handle`或`email`必須擇一

### Response
```
{
  citizen_id
  handle
  album_id
  persona_id
  personas: [ // 這個citizen的所有persona
    {
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
    ...
  ]
  roles: [ // active persona的所有role
    {
      channel
      tags: []
      name
    }
    ...
  ]
  token
}
```
