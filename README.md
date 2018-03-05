# [Watchout API Documentation](https://core-docs.watchout.tw/)

### 圖例
```
🌱　僅有標題
🌿　部分內容
🌳　完整內容
```

## 身分認證 Authentication

### 註冊
- [/auth/join](./auth/join) 🌱

### 登入
- [/auth/login](./auth/login) 🌱

## 草民 Citizen
> 關於草民的 API endpoints

### 草民資訊
- [/citizen](./citizen/citizen) 🌱
- []

### Email
- [/citizen/:handle/emails](./citizen/emails) 🌱
- [/citizen/:handle/emails/:emailID/request_verification](./citizen/emails#request-verification) 🌱
- [/citizen/:handle/emails/:emailID/confirm_verification/:token](./citizen/emails#confirm-verification) 🌱
- [/citizen/:handle/emails/:emailID/visibility](./citizen/emails#set-visibility) 🌱
- [/citizen/:handle/emails/:emailID/set_primary](./citizen/emails#set-primary) 🌱

### 密碼
- [/citizen/password](./citizen/password) 🌿
- [/citizen/request_reset_password](./citizen/password) 🌿
- [/citizen/reset_password](./citizen/password) 🌿

### 言論
- [/citizen/speeches](./citizen/speeches) 🌿

## 中央公園 Park

### 民調
- [/park/polls](./park/polls) 🌿

### 言論
- [/park/citizen_speech_targets](./park/citizen_speech_targets) 🌿
- [/park/citizen_speeches](./park/citizen_speeches) 🌿

## 給問擂台 Ask

### Games & Matches
- [/ask/games](./ask/games) 🌿
- [/ask/matches](./ask/matches) 🌿

### Questions & Answers
- [/ask/questions](./ask/questions) 🌿
- [/ask/answers](./ask/answers) 🌿

## 野生國會 c0ngress

### 委員 Reps
- [/c0ngress/reps](./c0ngress/reps) 🌿

### 政黨、黨團 Parties & Caucuses
- [/c0ngress/parties](./c0ngress/parties) 🌿
- [/c0ngress/caucuses](./c0ngress/caucuses) 🌿

### 委員表態 Rep Speeches
- [/c0ngress/rs_statements](./c0ngress/rs_statements) 🌿
- [/c0ngress/rs_bills](./c0ngress/rs_bills) 🌿
- [/c0ngress/rs_votes](./c0ngress/rs_votes) 🌿

### 法案 Acts
- [/c0ngress/acts](./c0ngress/acts) 🌿

### 工具 Utilities
- 日期、會期
  - [/c0ngress/date_to_term](./c0ngress/utilities#date-to-term) 🌳
  - [/c0ngress/date_to_rep_info](./c0ngress/utilities#date-to-rep-info) 🌳
  - [/c0ngress/unique_sessions](./c0ngress/utilities#unique-sessions) 🌳
  - [/c0ngress/unique_temp_sessions](./c0ngress/utilities#unique-temp-sessions) 🌳
- 選區
  - [/c0ngress/zones](./c0ngress/utilities#zones) 🌳
  - [/c0ngress/unique_districts](./c0ngress/utilities#unique-districts) 🌳
- 政府機關
  - [/c0ngress/gov_agencies](./c0ngress/utilities#government-agencies) 🌳
- 立法流程
  - [/c0ngress/legislative_steps](./c0ngress/utilities#legislative-steps) 🌳

## 內容組成 Composition

- [/comp/timelines](./comp/timelines) 🌿
- [/comp/figures](./comp/figures) 🌿

## 議題實驗室 Lab

### 基本設定
- [/lab/specific_topics](./lab/specific_topics) 🌿
- [/lab/st_questions](./lab/st_questions) 🌿

### 議題綜覽
- [/lab/topic_overviews](./lab/topic_overviews) 🌿

### 數據分析報告
- [/lab/data_reports](./lab/data_reports) 🌿

## 中控室／內容組成 Console-Composition

- [/console/comp/timelines](./console-comp/timelines) 🌿
- [/console/comp/timeline_events](./console-comp/timeline_events) 🌿
- [/console/comp/figures](./console-comp/figures) 🌿

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

### 委員表態 Rep Speeches
- 發言 Statements
  - [/console/lab/rs_statements](./console-lab/rs_statements) 🌳
- 提案、連署 Bills & Sponsorships
  - [/console/lab/rs_bills](./console-lab/rs_bills) 🌳
- 表決 Votes
  - [/console/lab/rs_votes](./console-lab/rs_votes) 🌳

### 議題實驗室 Lab
- 議題綜覽 Topic Overviews
  - [/console/lab/lab_topic_overviews](./console-lab/lab_topic_overviews) 🌳
- 分析評論 Insights
  - [/console/lab/lab_insights](./console-lab/lab_insights) 🌳
- 提案資料集 Bill Data Sets
  - [/console/lab/lab_bill_data_sets](./console-lab/lab_bill_data_sets) 🌳
- 發言資料集 Statement Data Sets
  - [/console/lab/lab_statement_data_sets](./console-lab/lab_statement_data_sets) 🌳
- 數據分析報告 Data Reports
  - [/console/lab/lab_data_reports](./console-lab/lab_data_reports) 🌳
