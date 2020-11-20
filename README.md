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

# テーブル設計

## users テーブル

| Column       | Type    | Options     |
| ------------ | ------- | ----------- |
| nickname     | string  | null: false |
| email        | string  | null: false |
| password     | string  | null: false |
| name         | string  | null: false |
| name_reading | string  | null: false |
| birthday     | integer | null: false |

### Association

- has_many :items
- has_many :orders

## items テーブル

| Column                    | Type    | Options     |
| ------------------------- | --------------------- | 
| item_explain              | text    | null: false |
| item_name                 | string  | null: false |
| item_category             | string  | null: false |
| item_sales_status         | string  | null: false |
| item_shipping_fee_status  | integer | null: false |
| item_prefecture           | integer | null: false |
| item_scheduled_delivery   | integer | null: false |
| price                     | integer | null: false |


### Association
- has_one :orders
- belongs_to :user

## order テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| user_id   | references | null: false, foreign_key: true |
| item_id   | references | null: false, foreign_key: true |
| day       | integer    | null: false                    |

### Association

- belongs_to :user
- belongs_to :item
- has_many :addresses

## addresses テーブル

| Column        | Type    | Options     |
| ------------- | ------- | ----------- |
| post_code     | integer | null: false |
| prefecture    | string  | null: false |
| city          | string  | null: false |
| house_number  | integer | null: false |
| building_name | string  | null: false |
| order_id      | integer | null: false |

### Association

- belongs_to :order