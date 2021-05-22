## users テーブル
| Column           | Type   | Options     |
| ---------------- | ------ | ----------- |
| nickname         | string | null: false |
| email            | string | null: false |
| password         | string | null: false |
| first_name       | string | null: false |
| family_name      | string | null: false |
| read_first_name  | string | null: false |
| read_family_name | string | null: false |
| birthday         | date   | null: false |

### Association

- has_many :items
- has_many :item_purchases


## items テーブル
| Column          | Type       | Options     |
| --------------- | ---------- | ----------- |
| photo           | text       | null: false |
| name            | string     | null: false |
| explanation     | text       | null: false |
| category        | integer    | null: false |
| condition       | integer    | null: false |
| shipment_source | integer    | null: false |
| shipment_day    | integer    | null: false |
| charge          | integer    | null: false |
| user            | references | null: false |
| price           | integer    | null: false | 

### Association

- belongs_to :user
- has_one :item_purchase


## item_purchase テーブル
| Column               | Type    | Options                        |
| -------------------- | ------- | ------------------------------ |
| item                 | integer | null: false, foreign_key: true |
| user                 | integer | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- belongs_to :purchase_information


## purchase_information テーブル
| Column        | Type    | Options                        |
| ------------- | ------- | ------------------------------ |
| postal_code   | string  | null: false                    |
| prefecture    | integer | null: false                    |
| city          | string  | null: false                    |
| address       | string  | null: false                    |
| phone_number  | string  | null: false                    |
| item_purchase | integer | null: false, foreign_key: true |

### Association

- has_one :item_purchase
