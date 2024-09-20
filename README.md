## usersテーブル

| Column             | Type    | Options     |
| ------------------ | ------  | ----------- |
| name               | string  | null: false |
| email              | string  | null: false, unique: true |
| encrypted_password | string  | null: false |

### Association
  has_many :tasks
  has_many :categories
  has_many :achievements


## tasksテーブル

| Column             | Type        | Options     |
| ------------------ | ------      | ----------- |
| user               | references  | null: false, foreign_key: true |
| category           | references  | null: false, foreign_key: true |
| title              | string      | null: false |
| description        | text        | null: false |
| due_date           | datetime    | null: false |
| priority           | string      | null: false |
| status             | string      | null: false |

### Association
  belongs_to :user
  belongs_to :category
  has_many :reminders

## categoryテーブル

| Column             | Type      | Options     |
| ------------------ | ------    | ----------- |
| user               | references| null: false, foreign_key: true |
| name               | string    | null: false, unique: true |
| color              | string    | null: false |

### Association
  belongs_to :user
  has_many :tasks

## reminderテーブル

| Column             | Type      | Options     |
| ------------------ | ------    | ----------- |
| task               | references| null: false, foreign_key: true |
| remind_at          | datetime  | null: false, unique: true |

### Association
  belongs_to :task
## achievementテーブル

| Column             | Type      | Options     |
| ------------------ | ------    | ----------- |
| user               | references| null: false, foreign_key: true |
| name               | string    | null: false, unique: true |
| description        | string    | null: false |
| points             | string    | null: false |

### Association
belongs_to :user