# README

***
## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|integer|null: false, foreign_key: true,add_index|
|user_id|integer|null: false, foreign_key: true,add_index|

### Association
- belongs_to :group
- belongs_to :user

***

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|text|null: false|

### Association
- has_many :messages
- has_many :members
- has_many :users , through: :members

***

## userテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: turue, add_index|
|email|string|null: false, unique: turue|
|password|string|null: false|

### Association
- has_many :messages
- has_many :members
- has_many :groups , through: :members

***

## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

