# Login
```
POST /auth/login
```

### Auth
NO

### Paging
NO

### Login With Handle Or Email

#### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `handle` | string | 🌕 `[1]` | 草民代號 |
| `email` | string | 🌕 `[1]` | Email |
| `password` | string | 🌕 | 密碼 |

`[1]`
> `handle`或`email`必須擇一

#### Sample Input

```json
{
  "handle": "watchout",
  "password": "password"
}
```

Or

```json
{
  "email": "user@watchout.tw",
  "password": "password"
}
```

### Login With Token

#### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `token` | string | 🌕 | 草民登入的token |
| `persona_id` | integer | 🌑 `[2]` | 草民的 persona ID |

`[2]`
> 設計用於切換當前 persona 使用

#### Sample Input

```json
{
  "token": "XXXXXXXX.DDDDDDDDDD.YYYYYYYYYY",
  "persona_id": 9527
}
```

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
