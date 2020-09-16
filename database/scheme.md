# DB


## === Clients block ========================

**clients**

- id            | PK | increment
- name          |    | char(50)
- lastname      |    | char(50)
- patronymic    |    | char(50)
- sex           |    | char(1)
- data_of_birth |    | data( date )
- id_city       | FK | longint
- street        |    | char(60)
- num_house     |    | int
- num_flat      |    | int
- datetime_reg  |    | date( datetime_stamp )

**clients_accounts**

- id                | PK | increment
- id_client         | FK | longint
- id_account_type   | FK | longint
- account_number    |    | char( 0000 0000 0000 0000 0000 )
- balance           |    | money
- account_date_open |    | date( date_stamp )

**clients_cards**

- id                | PK | increment
- id_client_account | FK | longint
- id_card_type      | FK | longint
- card_number       |    | char( 0000 0000 0000 0000 )
- card_data_open    |    | data( date )
- card_cvc          |    | char( 000 )
- card_name         |    | char(50)
- card_lastname     |    | char(50)

**clients_credits**

- id             | PK | increment
- id_client      | FK | longint
- id_credit_type | FK | longint
- pay_sum        |    | money

**clients_passports**

- id                    | PK | increment
- id_client             | FK | longint
- pass_name             |    | char(50)
- pass_lastname         |    | char(50)
- pass_patronymic       |    | char(50)
- pass_personal_code    |    | char( 000 )
- pass_num              |    | char( 00 00 )
- pass_serial           |    | char( 000000 )
- pass_issued_by        |    | char(100)
- pass_date_of_issue    |    | date( date )
- pass_subdivition_code |    | char( 000-000 )
- pass_date_of_birch    |    | date( date )
- pass_place_of_birch   |    | char(255)
- pass_photo            |    | OLE
- pass_date_add         |    | date( date_stamp )

**clients_telefons**

- id        | PK | increment
- id_client | FK | longint
- tel_num   |    | char( 0 (000) 000-00-00 )


## === Workers block ========================

**workers**

- id            | PK | increment
- name          |    | char(50)
- lastname      |    | char(50)
- partronymic   |    | char(50)
- sex           |    | char(1)
- data_of_birth |    | date( date )
- id_city       | FK | longint
- street        |    | char(60)
- num_house     |    | int(0)
- num_flat      |    | int(0)
- datetime_reg  |    | date( datetime_stamp )

**workers_otdels**

- id        | PK | increment
- id_worker | FK | longint
- id_otdel  | FK | longint

**workers_posts**

- id        | PK | increment
- id_worker | FK | longint
- id_post   | FK | longint


## === Data block ========================

**data_posts**

- id            | PK | increment
- post          |    | char(60)
- description   |    | text
- salary        |    | money
- work_schedule |    | text

**data_account_types**

- id          | PK | increment
- type        |    | char(20)
- description |    | text

**data_otdel_names**

- id          | PK | increment
- name        |    | char(40)
- description |    | text
- tasks       |    | text

**data_credit_types**

- id             | PK | increment
- name           |    | char(40)
- description    |    | text
- credit_sum     |    | money
- credit_percent |    | int( percent )

**data_card_types**

- id          | PK | increment
- name        |    | char(20)
- description |    | text
- max_sum     |    | money


## === Geo block ========================

**geo_city**

- id         | PK | increment
- id_country | FK | longint
- city       |    | char(50)

**geo_countries**

- id      | PK | increment
- country |    | char(50)


## === Сoverage block ========================

**coverage_bankomats**

- id            | PK | increment
- id_department | FK | longint
- balance       |    | money
- is_work       |    | boolean

**coverage_departments**

- id        | PK | increment
- id_city   | FK | longint
- street    |    | char(60)
- num_house |    | int

**coverage_otdels**

- id            | PK | increment
- id_department | FK | longint
- id_otdel_name | FK | longint
- work_spaces   |    | int
