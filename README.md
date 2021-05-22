## users テーブル
| Column             | Type   | Options      |
| ---------------- --| ------ | ------------ |
| nickname           | string | null: false  |
| email              | string | unique: true |
| encrypted_password | string | null: false  |
| first_name         | string | null: false  |
| family_name        | string | null: false  |
| read_first_name    | string | null: false  |
| read_family_name   | string | null: false  |
| birthday           | date   | null: false  |

### Association

- has_many :items
- has_many :item_purchases


## items テーブル
| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| name               | string     | null: false                    |
| explanation        | text       | null: false                    |
| category_id        | integer    | null: false                    |
| condition_id       | integer    | null: false                    |
| shipment_source_id | integer    | null: false                    |
| shipment_day       | integer    | null: false                    |
| charge             | integer    | null: false                    |
| user               | references | null: false, foreign_key: true |
| price              | integer    | null: false                    | 

### Association

- belongs_to :user
- has_one :item_purchase


## item_purchase テーブル
| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| item   | references | null: false, foreign_key: true |
| user   | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :purchase_information


## purchase_information テーブル
| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| postal_code   | string     | null: false                    |
| prefecture_id | integer    | null: false                    |
| city          | string     | null: false                    |
| address       | string     | null: false                    |
| building      | string     |                                |
| phone_number  | string     | null: false                    |
| item_purchase | references | null: false, foreign_key: true |

### Association

- belongs_to :item_purchase
