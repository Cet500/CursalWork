# DB


## === Clients block ========================

**clients**

- id
- name
- lastname
- patronymic
- sex
- data_of_birth
- id_city
- street
- num_house
- num_flat
- datatime_reg

**clients_telefons**

- id
- id_client
- tel_num

**clients_accounts**

- id
- id_client
- id_account_type
- account_number ( 0000 0000 0000 0000 0000 )
- balance
- account_data_open

**clients_cards**

- id
- id_client_account
- id_card_type
- card_number ( 0000 0000 0000 0000 )
- card_data_open
- card_cvc
- card_name
- card_lastname

**clients_passports**

- id
- id_client
- pass_name
- pass_lastname
- pass_patronymic
- pass_personal_code
- pass_num ( 00 00 )
- pass_serial ( 000000 )
- pass_issued_by
- pass_date_of_issue
- pass_subdivition_code ( 000-000 )
- pass_date_of_birch
- pass_place_of_birch
- pass_photo

**clients_credits**

- id
- id_client
- id_credit_type
- pay_sum


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
