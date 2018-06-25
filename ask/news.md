# News of Game in ASK

一場Game 的一週動態

- [Get questions of persona concerned topic](#get-questions-of-persona-concerned-topic)
- [Get the exporing questions](#Get-exporing-questions)
- [Get the questions being answered](#Get-the-questions-being-answered)
- [Get the popular quesitons](#get-popular-questions)
- [Get the editor choice](#get-the-editor-choice)

## Get questions of persona concerned topic

列出一週內 Active Persona 關心的(註1) 的議題中，相關的，而且是 Active Persona 尚未連署過的提問(註2)。

註1 : 記錄於 "Persona_Concerned_Topic" Table 中

註2 : 目的希望讓草民去連署更多的提問

### URI

```
GET /ask/games/:gameSlug/news/questions_persona_care
```

### Auth

- “automata”

### Paging

NO

### Response

```
{
  rows: [
    question object // [1]
    ,
    ...
  ],
  totalRowCount: 10
}
```

`[1]`
> From ASK_Question_Assigned_Persona

## Get the exporing questions

列出一週內近期快要到期的提問

### URI

```
GET /ask/games/:gameSlug/news/exporing_questions
```

### Auth

- “automata”

### Paging

NO

### Response

```
{
  rows: [
    question object // [1]
    ,
    ...
  ],
  totalRowCount: 10
}
```

## Get answered questions

列出一週內有被回答的問題 ( active_persona 有連署的優先)

### URI

```
GET /ask/game/:gameSlug/news/answered_question
```

### Auth

- “automata”

### Paging

NO

### Response

```
{
  rows: [
    question object // [1]
    ,
    ...
  ],
  totalRowCount: 10
}
```

## Get popular questions

列出一週內熱門的問題 (連署數高的)

### URI

```
GET /ask/game/:gameSlug/news/popular
```

### Auth

NO

### Paging

NO

### Response

```
{
  rows: [
    question object // [1]
    ,
    ...
  ],
  totalRowCount: 10
}
```

## Get editor choice questions

列出一週內熱門的問題 (排序從連署數高優先)

### URI

```
GET /ask/game/:gameSlug/news/editor_choice
```

### Auth

NO

### Paging

NO

### Response

```
{
  rows: [
    question object // [1]
    ,
    ...
  ],
  totalRowCount: 10
}
```