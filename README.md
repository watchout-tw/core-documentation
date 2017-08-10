# [Watchout API Documentation](https://core-docs.watchout.tw/)

## 草民 Citizen
> 關於草民的 API endpoints

### 註冊
- [/auth/join](./auth/join)

### 身分認證
- [/auth/login](./auth/login)

### 草民
- [/citizen/:handle](./citizen/id) 🌱
- [/citizen/:handle/password](./citizen/password) 🌱
- [/citizen/:handle/emails](./citizen/emails) 🌱
- [/citizen/:handle/emails/:emailID/request_verification](./citizen/emails#request-verification) 🌱
- [/citizen/:handle/emails/:emailID/confirm_verification/:token](./citizen/emails#confirm-verification) 🌱
- [/citizen/:handle/emails/:emailID/visibility](./citizen/emails#set-visibility) 🌱
- [/citizen/:handle/emails/:emailID/set_primary](./citizen/emails#set-primary) 🌱

## 影子立法院 c0ngress

### 政黨
- [/c0ngress/parties](./c0ngress/parties) 🌿

## 中央公園 Park

### 民調
- [/park/polls](./park/polls) 🌿

### 言論
- [/park/citizen_speech_targets](./park/citizen_speech_targets) 🌿
- [/park/citizen_speeches](./park/citizen_speeches) 🌿

## 中控室／議題實驗室 Console-Lab
> 中控室中與《議題實驗室》相關的 API endpoints

### 立法院 Legislative Yuan
- 屆期、會期 Terms & Sessions
  - [/console/lab/terms](./console-lab/terms) 🌳
  - [/console/lab/term_sessions](./console-lab/term_sessions)
  - [/console/lab/term_parties](./console-lab/term_parties)
  - [/console/lab/term_caucuses](./console-lab/term_caucuses)
  - [/console/lab/term_districts](./console-lab/term_districts)
- 委員會 Committees
  - [/console/lab/committees](./console-lab/committees) 🌳
- 委員 Representatives
  - [/console/lab/reps](./console-lab/reps) 🌳
- 政黨、黨團、政團 Parties & Caucuses
  - [/console/lab/parties](./console-lab/parties) 🌳
  - [/console/lab/caucuses](./console-lab/caucuses) 🌳

### 議題及法案 Topics & Acts
- 議題 Topics
  - [/console/lab/general_topics](./console-lab/general_topics) 🌳
  - [/console/lab/specific_topics](./console-lab/specific_topics) 🌳
- 議題關係 Topic Relations
  - [/console/lab/topic_relations](./console-lab/topic_relations)
- 法案 Acts
  - [/console/lab/acts](./console-lab/acts) 🌳
  - [/console/lab/act_dirs](./console-lab/act_dirs)
  - [/console/lab/act_features](./console-lab/act_features) 🌳
- 爭點 Questions
  - [/console/lab/st_questions](./console-lab/st_questions)

### 委員表態 Representatives’ Speeches
- 發言 Statements
  - [/console/lab/rs_statements](./console-lab/rs_statements) 🌳
- 提案、連署 Bills & Sponsorships
  - [/console/lab/rs_bills](./console-lab/rs_bills) 🌳
- 表決 Votes
  - [/console/lab/rs_votes](./console-lab/rs_votes) 🌳

### 工具 Utilities
- 日期
  - [/console/lab/date_to_term](./console-lab/utilities#date-to-term) 🌳
  - [/console/lab/date_to_rep_info](./console-lab/utilities#date-to-rep-info) 🌳
- 會期
  - [/console/lab/unique_sessions](./console-lab/utilities#unique-sessions) 🌳
  - [/console/lab/unique_temp_sessions](./console-lab/utilities#unique-temp-sessions) 🌳
- 選區
  - [/console/lab/zones](./console-lab/utilities#zones) 🌳
  - [/console/lab/unique_districts](./console-lab/utilities#unique-districts) 🌳
- 政府機關
  - [/console/lab/gov_agencies](./console-lab/utilities#government-agencies) 🌳
- 立法流程
  - [/console/lab/legislative_steps](./console-lab/utilities#legislative-steps) 🌳
