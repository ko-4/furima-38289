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
# furima-38289 ER図

## users テーブル

| Column             | Type       | Options                         |
| ------------------ | ---------- | ------------------------------- |
| nickname           | string     | null: false,                    |
| email              | string     | null: false, unique: true       |
| encrypted_password | string     | null: false                     |
| last_name          | string     | null: false                     |
| first_name         | string     | null: false                     |
| last_name_kana     | string     | null: false                     |
| first_name_kana    | string     | null: false                     |
| birthday           | date       | null: false                     |

has_many  :items
has_many  :buy_records

## items テーブル

| Column             | Type       | Options                         |
| ------------------ | ---------- | ------------------------------- |
| user               | references | null: false , foreign_key: true |
| item_name          | string     | null: false                     |
| item_info          | text       | null: false                     |
| category_id        | integer    | null: false                     |
| status_id          | integer    | null: false                     |
| load_id            | integer    | null: false                     |
| prefecture_id      | integer    | null: false                     |
| shipment_id        | integer    | null: false                     |
| item_place         | integer    | null: false                     |

belongs_to :user
has_one :buy_record


## buy_records(購入記録) テーブル

| Column             | Type       | Options                         |
| ------------------ | ---------- | ------------------------------- |
| user               | references | null: false, foreign_key: true  |
| item               | references | null: false, foreign_key: true  |

belongs_to :user
belongs_to :item
has_one :shipping_address

## shipping_address(発送先) テーブル

| Column             | Type       | Options                         |
| ------------------ | ---------- | ------------------------------- |
| post_num           | string     | null: false                     |
| prefecture_id      | integer    | null: false                     |
| municipalities     | string     | null: false                     |
| address            | string     | null: false                     |
| building           | string     |                                 |
| tell               | string     | null: false                     |
| buy_record         | references | null: false, foreign_key: true  |

belongs_to :buy_record