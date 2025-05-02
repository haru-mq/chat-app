# テーブル設計

## users table

| Column              | Type    | Options     |
| ------------------- | ------  | ----------- |
| name                | string  | null: false |
| email               | string  | null: false, unique: true |
| encrypted_password  | string  | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## rooms table

| Column  | Type    | Options     |
| ------- | ------  | ----------- |
| name    | string  | null: false |

### Association

- has_many :room_users
- has_many :users, through: :room_users
- has_many :messages

## room_users table

| Column  | Type        | Options                         |
| ------  | ----------  | ------------------------------  |
| user    | references  | null: false, foreign_key: true  |
| room    | references  | null: false, foreign_key: true  |

### Association

- belongs_to :room
- belongs_to :user

## messages table

| Column  | Type        | Options                         |
| ------- | ----------- | ------------------------------  |
| content | string      |                                 |
| user    | references  | null: false, foreign_key: true  |
| room    | references  | null: false, foreign_key: true  |

### Association

- belongs_to :room
- belongs_to :user