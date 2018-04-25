# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index|
|mail|string|null: false, unique: true|

### Association
- has_many :members
- has_many :messages
- has_many :groups,through: :members

## membersテーブル（中間テーブル）

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :groups
- belongs_to :users

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :members
- has_many :messages
- has_many :users,through: :members

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|integer|null: true, foreign_key: true|
|user_id|integer|null: true, foreign_key: true|

### Association
- belongs_to :members
- belongs_to :groups




