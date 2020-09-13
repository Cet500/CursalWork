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
- datetime_reg  |    | date( datetime )

**clients_telefons**

- id        | PK | increment
- id_client | FK | longint
- tel_num   |    | char( 0 (000) 000-00-00 )

**clients_accounts**

- id                | PK | increment
- id_client         | FK | longint
- id_account_type   | FK | longint
- account_number    |    | char( 0000 0000 0000 0000 0000 )
- balance           |    | money
- account_date_open |    | date( date )

**clients_cards**

- id                | PK | increment
- id_client_account | FK | longint
- id_card_type      | FK | longint
- card_number       |    | char( 0000 0000 0000 0000 )
- card_data_open    |    | data( date )
- card_cvc          |    | char( 000 )
- card_name         |    | char(50)
- card_lastname     |    | char(50)

**clients_passports**

- id                    | PK | increment
- id_client             | FK | longint
- pass_name             |    | 
- pass_lastname         |    | 
- pass_patronymic       |    | 
- pass_personal_code    |    | 
- pass_num              |    | char( 00 00 )
- pass_serial           |    | char( 000000 )
- pass_issued_by        |    | 
- pass_date_of_issue    |    | 
- pass_subdivition_code |    | char( 000-000 )
- pass_date_of_birch    |    | 
- pass_place_of_birch   |    | 
- pass_photo            |    | 

**clients_credits**

- id             | PK | increment
- id_client      | FK | longint
- id_credit_type | FK | longint
- pay_sum        |    | 


## === Workers block ========================

**workers**

- id
- name
- lastname
- partronymic
- sex
- data_of_birth
- id_city
- street
- num_house
- num_flat

**workers_posts**

- id
- id_worker
- id_post

**workers_otdels**

- id
- id_worker
- id_otdel


## === Data block ========================

**data_posts**

- id
- post
- description
- salary
- work_schedule

**data_account_types**

- id
- type
- description

**data_otdel_names**

- id
- name
- description
- tasks

**data_credit_types**

- id
- name
- description
- credit_sum
- credit_percent

**data_card_types**

- id
- name
- description
- max_sum


## === Geo block ========================

**geo_countries**

- id
- country

**geo_city**

- id
- id_country
- city


## === Сoverage block ========================

**coverage_departments**

- id
- id_city
- street
- num_house

**coverage_otdels**

- id
- id_department
- id_otdel_name
- work_spaces

**coverage_bankomats**

- id
- id_department
- balance
- is_work
