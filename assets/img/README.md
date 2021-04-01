# テーブル設計

![TeachingBuddyのER図]()

## users テーブル

| Column             | Type   | Options 	               |
| :--------------    | :----- | :----------------------- |
| nickname           | string | null: false              |
| encrypted_password | string | null: false              |
| email              | string | null: false,unique:true  |
| last_name          | string | null: false              |
| first_name         | string | null: false              |
| last_name_kana     | string | null: false              |
| first_name_kana    | string | null: false              |
| birthday		       | date   | null: false              |

### Association

- has_many :items
- has_many :orders

## items テーブル

| Column         | Type  		 | Options 	           |
| :------------  | :------------ | :--------------- |
| name           | string  		  | null: false      |
| info           | text   		    | null: false      |
| category_id    | integer       | null: false      |
| status_id      | integer       | null: false      |
| shippingfee_id | integer       | null: false      |
| shipplace_id    | integer       | null: false      |
| dateship_id    | integer		    | null: false      |
| price          | integer       | null: false      |
| user           | references    | foreign_key: true |

### Association

- belongs_to :user
- has_one :order

## orders テーブル

| Column         | Type  		    | Options 	        |
| :------------- | :----------- | :---------------- |
| user           | references   | foreign_key: true |
| item           | references   | foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :address

## addresses テーブル

| Column         | Type  	    	| Options           |
| :------------- | :----------- | :---------------- |
| zip_code       | string  		  | null: false       |
| shipplace_id   | integer      | null: false       |
| city           | string       | null: false       |
| blocknum       | string       | null: false       |
| building       | string       |                   |
| tel            | string       | null: false       |
| order          | references   | foreign_key: true |

### Association

- belongs_to :order