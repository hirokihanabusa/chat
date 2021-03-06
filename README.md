# DB設計

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true, unique: true|

### Association
- has_many :groups_user
- has_many :users, through: :groups_users
- has_many :messages


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true, unique: true|
|email|string|null: false|
|encrypted_password|string|null: false, unique: true|

### Association
- has_many :groups_user
- has_many :groups, through: :groups_users
- has_many :messages


## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|group_id|references|null: false, foreign_key: true|
|user_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :groups
