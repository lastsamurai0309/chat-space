## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index:true|
|email|string|null: false, unique:true|
|password|string|null: false|

### Association
- has_many :groups_users
- has_many :messages
- has_many :groups,throught:groups_users

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|user_ID|integer|null: false,foreign_key: true|
|group_ID|integer|null: false,foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|title|string|null: false|

### Association
- has_many :groups_users
- has_many:messages
- has_many :users,through: groups_users