# [Watchout Core API 文件目錄 Documentation Index](https://core-docs.watchout.tw/)

## 草民 Citizen
> 關於草民的 API endpoints

### 註冊
- [/auth/join](./auth/join)

### 身分認證
- [/auth/login](./auth/login)

### 草民
- [/citizen/:handle](./citizen/id)
- [/citizen/:handle/password](./citizen/password)
- [/citizen/:handle/emails](./citizen/emails)
- [/citizen/:handle/emails/:emailID/request_verification](./citizen/emails#request-verification)
- [/citizen/:handle/emails/:emailID/confirm_verification/:token](./citizen/emails#confirm-verification)
- [/citizen/:handle/emails/:emailID/visibility](./citizen/emails#set-visibility)
- [/citizen/:handle/emails/:emailID/set_primary](./citizen/emails#set-primary)

## 中控室／議題實驗室 Console/Lab
> 中控室中與《議題實驗室》相關的 API endpoints

### 立法院 Legislative Yuan
- 屆期、會期 Terms & Sessions
  - [/console/lab/terms](./console-lab/terms)
  - [/console/lab/term_sessions](./console-lab/term_sessions)
  - [/console/lab/term_parties](./console-lab/term_parties)
  - [/console/lab/term_caucuses](./console-lab/term_caucuses)
  - [/console/lab/term_districts](./console-lab/term_districts)
- 委員會 Committees
  - [/console/lab/committees](./console-lab/committees)
- 委員 Representatives
  - [/console/lab/reps](./console-lab/reps)
- 選區 Districts

- 政團、黨團 Parties & Caucuses
  - [/console/lab/parties](./console-lab/parties)
  - [/console/lab/caucuses](./console-lab/caucuses)

### 議題及法案 Topics & Acts
- 大議題 General Topics
  - [/console/lab/general_topics](./console-lab/general_topics)
- 小議題 Specific Topics
  - [/console/lab/specific_topics](./console-lab/specific_topics)
- 議題關係 Topic Relations
  - [/console/lab/topic_relations](./console-lab/topic_relations)
- 法案 Acts
  - [/console/lab/acts](./console-lab/acts)
  - [/console/lab/act_dirs](./console-lab/act_dirs)
  - [/console/lab/act_features](./console-lab/act_features)
- 爭點 Questions
  - [/console/lab/st_questions](./console-lab/st_questions)


### 委員表態 Representatives’ Speeches
- 發言 Statements
  - [/console/lab/rs_statements](./console-lab/rs_statements)
- 提案、連署 Bills & Sponsorships
  - [/console/lab/rs_bills](./console-lab/rs_bills)
- 表決 Votes
  - [/console/lab/rs_votes](./console-lab/rs_votes)

### 工具 Utilities
- 日期
  - [/console/lab/date_to_term](./console-lab/utilities#date-to-term)
- 選區
  - [/console/lab/zones](./console-lab/utilities#zones)
  - [/console/lab/district_unique_names](./console-lab/utilities#district-unique-names)
- 政府機關
  - [/console/lab/gov_agencies](./console-lab/utilities#government-agencies)
