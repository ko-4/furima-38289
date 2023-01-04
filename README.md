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
| nickname           | string     | null: false, unique: true       |
| mail_address       | string     | null: false, unique: true       |
| encrypted_password | string     | null: false,                    |
| kanji              | string     | null: false                     |
| katakana           | string     | null: false                     |
| birthday           | date       | null: false                     |

## items テーブル

| Column             | Type       | Options                         |
| ------------------ | ---------- | ------------------------------- |
| user               | references | null: false , foreign_key: true |
| image              | references | null: false                     |
| item_name          | string     | null: false                     |
| setsumei           | text       | null: false, foreign_key: true  |
| category           | string     | null: false, unique: true       |
| status             | string     | null: false                     |
| load               | string     | null: false                     |
| area               | string     | null: false                     |
| shipment           | string     | null: false                     |
| place              | integer    | null: false                     |

## buy_records(購入記録) テーブル

| Column             | Type       | Options                         |
| ------------------ | ---------- | ------------------------------- |
| user               | references | null: false, foreign_key: true  |
| shipping_address   | references | null: false, foreign_key: true  |
| item               | references | null: false, foreign_key: true  |

## shipping address(発送先) テーブル

| Column             | Type       | Options                         |
| ------------------ | ---------- | ------------------------------- |
| post_num           | integer    | null: false                     |
| prefectures        | string     | null: false                     |
| municipalities     | string     | null: false                     |
| address            | string     | null: false                     |
| building           | string     |                                 |
| tell               | integer    | null: false                     |