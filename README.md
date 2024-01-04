# -SubscTimeLy
 
# テーブル構造

## Usersテーブル
| Column             | Type   | Options                          |
| ------------------ | ------ | ---------------------------------|
| nick_name          | string | null: false                      |
| family_name        | string | null: false                      |
| first_name         | string | null: false                      |
| family_name_kana   | string | null: false                      |           
| first_name_kana    | string | null: false                      |
| email              | string | null: false, unique: true        |
| encrypted_password | string | null: false                      |

### Association
 has_many :user_subscriptions
 has_many :subscriptions, through: :user_subscriptions
 has_many :notifications

## Subscriptionsテーブル
| Column             | Type       | Options                          |
| ------------------ | ---------- | ---------------------------------|
| user               | references | null: false, foreign_key: true   |
| subsc_name_id      | integer    | null: false                      |
| start_date         | timestamps |                                  |           
| end_date           | timestamps |                                  |
| description        | text       | null : false                     |
| price              | string     | null: false                      |

### Association
 belongs_to :user
 has_many :user_subscriptions
 has_many :users, through: :user_subscriptions
 has_many :notifications

## user_subscriptions テーブル

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| user           | references | null: false, foreign_key: true |
| subscription   | references | null: false, foreign_key: true |

### Association
 belongs_to :user
 belongs_to :subscription

## Notificationsテーブル

| Column       | Type       | Options                        |
| ------------ | ---------- | ------------------------------ |
| user         | references | null: false, foreign_key: true |
| subscription | references | null: false, foreign_key: true |
| message      | text       | null: false                    |
| sent_at      | timestamps |                                |

### アソシエーション
 belongs_to :user
 belongs_to :subscription
