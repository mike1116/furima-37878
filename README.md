# DB 設計

## users table

| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| nickname           | string              | null: false               |
| email              | string              | null: false,unique: true  |
| encrypted_password | string              | null: false               |
| password_confirmation  | string              | null: false               |
| firstname          | string              | null: false               |
| lastname           | string              | null: false               |
| read_lastname      | string              | null: false               |
| read_firstname     | string              | null: false               |
| birth              | string              | null: false               |


### Association

* has_many :items
* has_many :records
* has_many :deliveries

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

- belongs_to :users
- has_one :records

## records table

| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| title                               | string        | null: false                    |
| profile                             | text          | null: false                    |
| user                                | references    | null: false, foreign_key: true |
| price                               | string        | null: false                    |
| saler_id                               | string     | null: false                    |
| buyer_id                               | string     | null: false                    |

### Association

- belongs_to :users
- has_one :items
- has_many :deliveries

## deliveries table

| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| post                  | string       | null: false                    |
| prefecture            | string       | null: false                    |
| municipalities        | string       | null: false                    |
| address               | string       | null: false                    |
| building_name         | string       | null: false                    |
| phone_number          | string       | null: false                    |

- belongs_to :records