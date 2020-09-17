# DB

## === Info ====

**Abbraviatures**

A - Auto-generate, require
R - Require

PK - Primary key
FK - Foreign key ( one to many )
FU - Foreign key unique ( one to one )
IU - Index unique
IN - Index non-unique

P - Placeholder
M - Mask
F - File
L - List of variants

## === Clients block ========================

**clients**

- id            | A | PK |   | increment
- name          | R |    |   | char(50)
- lastname      | R |    |   | char(50)
- patronymic    | R |    |   | char(50)
- sex           | R |    | L | char(1)
- data_of_birth | R |    |   | data( date )
- id_street     | R | FK | P | longint
- num_house     | R |    |   | int
- litera_house  |   |    |   | char(1)
- num_flat      | R |    |   | int
- post_index    |   |    | M | char( 000000 )
- datetime_reg  | A |    |   | date( datetime_stamp )

**clients_accounts**

- id                | A | PK |   | increment
- id_client         | R | FK | P | longint
- id_account_type   | R | FK | P | longint
- account_number    | R | IU | M | char( 0000 0000 0000 0000 0000 )
- balance           | A |    |   | money
- account_date_open | A |    |   | date( date_stamp )

**clients_cards**

- id                | A | PK |   | increment
- id_client_account | R | FK | P | longint
- id_card_type      | R | FK | P | longint
- card_number       | R | IU | M | char( 0000 0000 0000 0000 )
- card_data_open    | A |    |   | data( date )
- card_cvc          | R |    | M | char( 000 )
- card_name         | R |    |   | char(50)
- card_lastname     | R |    |   | char(50)

**clients_credits**

- id             | A | PK |   | increment
- id_client      | R | FK | P | longint
- id_credit_type | R | FK | P | longint
- pay_sum        | A |    |   | money

**clients_passports**

- id                    | A | PK |   | increment
- id_client             | R | FU | P | longint
- pass_name             | R |    |   | char(50)
- pass_lastname         | R |    |   | char(50)
- pass_patronymic       | R |    |   | char(50)
- pass_personal_code    |   |    | M | char( 000 )
- pass_num              | R |    | M | char( 00 00 )
- pass_serial           | R |    | M | char( 000000 )
- pass_issued_by        | R |    |   | char(100)
- pass_date_of_issue    | R |    |   | date( date )
- pass_subdivition_code | R |    | M | char( 000-000 )
- pass_date_of_birch    | R |    |   | date( date )
- pass_place_of_birch   | R |    |   | char(255)
- pass_photo            |   |    | F | OLE
- pass_date_add         | A |    |   | date( date_stamp )

**clients_telefons**

- id        | A | PK |   | increment
- id_client | R | FK | P | longint
- tel_num   | R | IU | M | char( 0 (000) 000-00-00 )


## === Workers block ========================

**workers**

- id            | A | PK |   | increment
- name          | R |    |   | char(50)
- lastname      | R |    |   | char(50)
- partronymic   | R |    |   | char(50)
- sex           | R |    | L | char(1)
- data_of_birth | R |    |   | date( date )
- id_street     | R | FK | P | longint
- num_house     | R |    |   | int(0)
- litera_house  |   |    |   | char(1)
- num_flat      | R |    |   | int
- post_index    |   |    | M | char( 000000 )
- datetime_reg  | A |    |   | date( datetime_stamp )

**workers_otdels**

- id        | A | PK |   | increment
- id_worker | R | FK | P | longint
- id_otdel  | R | FK | P | longint

**workers_posts**

- id        | A | PK |   | increment
- id_worker | R | FK | P | longint
- id_post   | R | FK | P | longint


## === Data block ========================

**data_posts**

- id            | A | PK |   | increment
- post          | R |    |   | char(60)
- description   |   |    |   | text
- salary        | R |    |   | money
- work_schedule | R |    |   | text

**data_account_types**

- id            | A | PK |   | increment
- type          | R |    |   | char(20)
- description   |   |    |   | text
- max_money_sum | R |    |   | money

**data_otdel_names**

- id          | A | PK |   | increment
- name        | R |    |   | char(40)
- description |   |    |   | text
- tasks       |   |    |   | text

**data_credit_types**

- id             | A | PK |   | increment
- name           | R |    |   | char(40)
- description    |   |    |   | text
- credit_sum     | R |    |   | money
- credit_percent | R |    |   | int( percent )

**data_card_types**

- id                  | A | PK |   | increment
- name                | R |    |   | char(20)
- description         |   |    |   | text
- max_money_operation | R |    |   | money


## === Geo block ========================

**geo_cities**

- id         | A | PK |   | increment
- id_country | R | FK | P | longint
- city       | R |    |   | char(50)

**geo_countries**

- id      | A | PK |   | increment
- country | R | IU |   | char(50)

**geo_streets**

- id      | A | PK |   | increment
- id_city | R | FK | P | longint
- street  | R |    |   | char(50)


## === Сoverage block ========================

**coverage_bankomats**

- id            | A | PK |   | increment
- id_department | R | FK | P | longint
- balance       | A |    |   | money
- is_work       | A |    |   | boolean

**coverage_departments**

- id        | A | PK |   | increment
- id_street | R | FK | P | longint
- name      | R |    |   | char(50)
- num_house | R |    |   | int

**coverage_otdels**

- id            | A | PK |   | increment
- id_department | R | FK | P | longint
- id_otdel_name | R | FK | P | longint
- work_spaces   | A |    |   | int
