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
|nickname|string|null: false|
|email|string|null: false,unique:true|
|password|string|null: false|
|image|string|

### Association
--has_many :groups,through: :groups_users
--has_many :groups_users
--has_many :comments
--has_many :posts


## postsテーブル
|Column|Type|Options|
|------|----|-------|
|content|text|null: false|
|photo|string|null: false|
|user_id|integer|null: false, foreign_key: true|


### Association
--belongs_to :user
--has_many :comments


## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|content|string|null: false|
|user_id|integer|null: false, foreign_key: true|
|post_id|integer|null: false, foreign_key: true|

### Association
--belongs_to :user
--belongs_to :post

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|content|text|null: false|

### Association
--has_many :users, through: :groups_users
--has_many :groups_users

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


