# テーブル設計

## user テーブル

| Column           | Type   | Options     |
| ---------------- | ------ | ----------- |
| nickname         | string | null: false |
| email            | string | null: false |
| password         | string | null: false |
| family_name      | string | null: false |
| first_name       | string | null: false |
| family_name_kana | string | null: false |
| first_name_kana  | string | null: false |
| birthday         | date   | null: false |

### Association

- has_many :items
- has_many :purchases

## item テーブル

| Column              | Type      | Options                        |
| ------------------- | --------- | ------------------------------ |
| name                | string    | null: false                    |
| description         | text      | null: false                    |
| image               | text      | null: false                    |
| category_id         | integer   | null: false                    |
| product_status_id   | integer   | null: false                    |
| delivery_fee_id     | integer   | null: false                    |
| ship_from_id        | integer   | null: false                    |
| time_to_ship        | integer   | null: false                    |
| price               | integer   | null: false                    |
| user                | reference | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :purchase

## purchase テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| item   | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :address

## address テーブル

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| postal_code    | string     | null: false                    |
| prefectures_id | integer    | null: false                    |
| city           | string     | null: false                    |
| house_number   | string     | null: false                    |
| building_name  | string     |                                |
| phone_number   | string     | null: false                    |
| purchase       | references | null: false, foreign_key: true |

### Association

- belongs_to :purchase