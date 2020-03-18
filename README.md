# Freemarket_DataBase_plan
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false, unique: true, index: true|
|last_name_kanji|string|null: false|
|first_name_kanji|string|null: false|
|last_name_kana|string|null: false|
|first_name_kana|string|null: false|
|birth_year|integer|null: false|
|birth_month|integer|null: false|
|birth_day|integer|null: false|

### Association
- belongs_to: shipping_info
- belongs_to: credit_card
- has_many: seller
- has_many: buyer
- has_many: items, through:  seller
- has_many: items, through: :buyer


## shipping_infoテーブル
|Column|Type|Options|
|------|----|-------|
|last_name_kanji|string|null: false|
|farst_name_kanji|string|null: false|
|last_name_kana|string|null: false|
|farst_name_kana|string|null: false|
|postalcode|integer|null: false|
|prefectures|string|null: false|
|municipalities|string|null: false|
|address|string|null: false|
|building_name|string||
|phone_number|integer|null: false|

### Association
- belongs_to: user

## creditcardsテーブル
|Column|Type|Options|
|------|----|-------|
|expiration_data_month|integer|null: false|
|expiration_data_year|integer	null: false|
|security_code|integer|null: false|
- belongs_to: user


## itemsテーブル
|Column|Type|Options|
|------|----|-------|

### Association
- has_many: pictures
- has_many: sellers
- has_many: users, through:  sellers
- has_many: buyers
- has_many: users, through: :buyers
- has_many: items_categories
- has_many: categories, through: :items_categories
- has_many: items_postages
- has_many: postages, through: :items_postages
- belongs_to: size
- belongs_to: bland
- belongs_to: item_status
- belongs_to: shipping_area
- belongs_to: delibery_date


## picturesテーブル
|Column|Type|Options|
|------|----|-------|
|picture|string|null: false|

### Association
- belongs_to: item


## sellersテーブル
|Column|Type|Options|
|------|----|-------|
|user|reference|null: false, foreign_key: true|
|item|reference|null: false, foreign_key: true|

### Association
- belongs_to: user
- belongs_to: item


## buyersテーブル
|Column|Type|Options|
|------|----|-------|
|user|reference|null: false, foreign_key: true|
|item|reference|null: false, foreign_key: true|

### Association
- belongs_to: user
- belongs_to: item


## items_categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|category|reference|null: false, foreign_key: true|

### Association
- belongs_to: item
- belongs_to: category


## categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|category|string|null: false|

### Association
- has_many: items, through: :items_categories


## sizesテーブル
|Column|Type|Options|
|------|----|-------|
|size|string|null: false|

### Association
- has_many: items


## blandsテーブル
|Column|Type|Options|
|------|----|-------|
|bland|string||

### Association
- has_many: items


## item_statusesテーブル
|Column|Type|Options|
|------|----|-------|
|status|string|null: false|

### Association
- has_many: items


## shipping_areasテーブル
|Column|Type|Options|
|------|----|-------|
|prefecture|string|null: false|

### Association
- has_many: items


## delibery_datesテーブル
|Column|Type|Options|
|------|----|-------|
|delibery_date|string|null: false|

### Association
- has_many: items


