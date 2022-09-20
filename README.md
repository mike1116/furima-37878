# DB 設計

## users table

| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| nickname           | string              | null: false               |
| email              | string              | null: false,unique: true  |
| encrypted_password | string              | null: false               |
| first_name          | string              | null: false               |
| last_name           | string              | null: false               |
| read_last_name      | string              | null: false               |
| read_first_name     | string              | null: false               |
| birth              | date              | null: false               |


### Association

* has_many :items
* has_many :records

## items table

| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| title                               | string     | null: false                    |
| profile                             | text       | null: false                    |
| user                                | references | null: false, foreign_key: true |
| price                               | string     | null: false                    |
| saler_id                               | string     | null: false                    |
| buyer_id                               | string     | null: false                    |


### Association

- belongs_to :user
- has_one :record

## records table

| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| title                               | string        | null: false                    |
| profile                             | text          | null: false                    |
| user                                | references    | null: false, foreign_key: true |
| category                            | string        | null: false                    |
| situation                           | string        | null: false                    |
| charge                              | string        | null: false                    |
| price                               | string        | null: false                    |
| area                                | string        | null: false                    |
| delively_day                        | string        | null: false                    |
| saler_id                            | string        | null: false                    |
| buyer_id                            | string        | null: false                    |

### Association

- belongs_to :user
- has_one :item
- has_one :delivery

## deliveries table

| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| post                  | string       | null: false                    |
| prefecture_id         | integer      | null: false                    |
| municipalities        | string       | null: false                    |
| address               | string       | null: false                    |
| building_name         | string       |                                |
| phone_number          | string       | null: false                    |
| user                  | references    | null: false, foreign_key: true |

- belongs_to :record