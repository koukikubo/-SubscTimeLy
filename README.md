## Usersテーブル

|Column|Type|Options|
- email  string   null: false
- encrypted_password  string  null: false

### Association
- has_many :user_subscriptions 
- has_many :subscriptions, through: :user_subscriptions

- has_many :notifications

## Subscriptionsテーブル
- user_id : integer null: false :サブスクリプションを登録したユーザーのID
- subsc_name :string null: false
- start_date :datetime null: false
- end_date   :datetime null: false
- subsc_price :integer null: false

### Association
- belongs_to :user : サブスクリプションは一つのユーザーに所属
- has_many :user_subscriptions
- has_many :users, through: :user_subscriptions : 一つのサブスクリプションが複数のユーザーを通じて所有

- has_many :notifications: 一つのサブスクリプションが複数の通知を持つ

## Notificationsテーブル

- user_id: 通知を受け取るユーザーのID
- subscription_id: 通知に関連するサブスクリプションのID
- message: 通知のメッセージ内容
- sent_at: 通知が送信された日時

### アソシエーション

- belongs_to :user: 通知は一つのユーザーに所属
- belongs_to :subscription: 通知は一つのサブスクリプションに所属
