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

| Column              | Type     | Options     |
| ------------------- | -------- | ----------- |
| nickname            | string   | null: false |
| email               | string   | null: false |
| encrypted_password  | string   | null: false |
| last_name           | string   | null: false |
| first_name          | string   | null: false |
| last_name_hurigana  | string   | null: false |
| first_name_hurigana | string   | null: false |
| birthday            | date     | null: false |

### Association

- has_many :items
- has_many :orders_historys

## items テーブル

| Column       | Type       | Options                      |
| -----------  | ---------- | ---------------------------- |
| user         | references | null: false,foreign_key:true |
| product_name | string     | null: false                  |
| explanation  | string     | null: false                  |
| category_id  | integer    | null: false                  |
| status_id    | integer    | null: false                  |
| burden_id    | integer    | null: false                  |
| area_id      | integer    | null: false                  |
| day_id       | integer    | null: false                  |
| price        | integer    | null: false                  |

### Association

- belongs_to :user
- has_one    :orders_history

## orders テーブル

| Column             | Type       | Options                         |
| ------------------ | ---------- | ------------------------------- |
| postal_code        | string     | null: false                     |
| area_id            | integer    | null: false                     |
| municipalities     | string     | null: false                     |
| address            | string     | null: false                     |
| building_name      | string     |                                 |
| phone_number       | string     | null: false                     |
| orders_history     | references | null: false,foreign_key:true |

### Association

- belongs_to :orders_history

## orders_history

| Column          | Type       | Options                       |
| --------------- | ---------- | ----------------------------- |
| user            | references | null: false,foreign_key: true |
| item            | references | null: false,foreign_key: true |

### Association

- belong_to   :user
- belong_to   :item
- has_one     :order