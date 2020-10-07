# DB


## === [en] Info ====

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
C - Calculate  
  
RA - Russian alias ( NOT NAME )

**Tables headers**

name - name of field  
a    - abbraviature  
ky   - key  
al   - alias  
type - type of field


## === [ru] Информация ====

**Расшифровка аббравиатур свойств полей**

A - Автоматически заполняемое поле, по-умолчанию обязательно к заполнению  
R - Обязательное к заполнению поле  
  
PK - Первичный ключ  
FK - Внешний ключ ( связь - один ко многим )  
FU - Уникальный внешний ключ ( связь - один к одному )  
IU - Уникальный индекс  
IN - Не уникальный индекс, с повторениями  
  
P - Поле с подменой значения ( заполнителем )  
M - Поле с маской ( форматом ) заполнения  
F - Поле с файлом  
L - Поле со списоком значений  
C - Вычисляемое поле  
  
RA - Русское название ( не имя поля, а лишь внешняя название )

**Расшифровка названий столбцов таблиц**

name - название поля  
a    - аббравиатура  
ky   - ключ  
al   - внешнее название поля  
type - тип поля


## === Clients block ========================

**clients**

Таблица с базовыми данными о клиентах.

| name          | a | ky | a | al | type                   |
|:--------------|:-:|:--:|:-:|:--:|:-----------------------|
| id            | A | PK |   |    | increment              |
| name          | R |    |   | RA | char(50)               |
| lastname      | R |    |   | RA | char(50)               |
| patronymic    | R |    |   | RA | char(50)               |
| sex           | R |    | L | RA | char(1)                |
| data_of_birth | R |    |   | RA | data( date )           |
| id_street     | R | FK | P | RA | longint                |
| num_house     | R |    |   | RA | int                    |
| litera_house  |   |    |   | RA | char(1)                |
| num_flat      | R |    |   | RA | int                    |
| post_index    |   |    | M | RA | char( 000000 )         |
| datetime_reg  | A |    |   |    | date( datetime_stamp ) |

---

**clients_accounts**

Таблица с счетами клиентов.

| name              | a | ky | a | al | type                             |
|:------------------|:-:|:--:|:-:|:--:|:---------------------------------|
| id                | A | PK |   |    | increment                        |
| id_client         | R | FK | P | RA | longint                          |
| id_account_type   | R | FK | P | RA | longint                          |
| account_number    | R | IU | M | RA | char( 0000 0000 0000 0000 0000 ) |
| balance           | A |    |   | RA | money                            |
| account_date_open | A |    |   | RA | date( date_stamp )               |

---

**clients_cards**

Таблица с картами, выданными клиентам банка.

| name              | a | ky | a | al | type                        |
|:------------------|:-:|:--:|:-:|:--:|:----------------------------|
| id                | A | PK |   |    | increment                   |
| id_client_account | R | FK | P | RA | longint                     |
| id_card_type      | R | FK | P | RA | longint                     |
| card_number       | R | IU | M | RA | char( 0000 0000 0000 0000 ) |
| card_data_open    | A |    |   | RA | data( date )                |
| card_cvc          | R |    | M | RA | char( 000 )                 |
| card_name         | R |    |   | RA | char(50)                    |
| card_lastname     | R |    |   | RA | char(50)                    |

---

**clients_credits**

Таблица с кредитами, выданными клиентам банка.

| name           | a | ky | a | al | type      |
|:---------------|:-:|:--:|:-:|:--:|:----------|
| id             | A | PK |   |    | increment |
| id_client      | R | FK | P | RA | longint   |
| id_credit_type | R | FK | P | RA | longint   |
| pay_sum        | A |    | C | RA | money     |

---

**clients_passports**

Таблица с паспортными данными клиентов.

| name                  | a | ky | a | al | type               |
|:----------------------|:-:|:--:|:-:|:--:|:-------------------|
| id                    | A | PK |   |    | increment          |
| id_client             | R | FU | P | RA | longint            |
| pass_name             | R |    |   | RA | char(50)           |
| pass_lastname         | R |    |   | RA | char(50)           |
| pass_patronymic       | R |    |   | RA | char(50)           |
| pass_personal_code    |   |    | M | RA | char( 000 )        |
| pass_num              | R |    | M | RA | char( 00 00 )      |
| pass_serial           | R |    | M | RA | char( 000000 )     |
| pass_issued_by        | R |    |   | RA | char(100)          |
| pass_date_of_issue    | R |    |   | RA | date( date )       |
| pass_subdivition_code | R |    | M | RA | char( 000-000 )    |
| pass_date_of_birch    | R |    |   | RA | date( date )       |
| pass_place_of_birch   | R |    |   | RA | char(255)          |
| pass_photo            |   |    | F | RA | OLE                |
| pass_date_add         | A |    |   |    | date( date_stamp ) |

---

**clients_telefons**

Таблица с телефонами клиентов.

| name      | a | ky | a | al | type                      |
|:----------|:-:|:--:|:-:|:--:|:--------------------------|
| id        | A | PK |   |    | increment                 |
| id_client | R | FK | P | RA | longint                   |
| tel_num   | R | IU | M | RA | char( 0 (000) 000-00-00 ) |


## === Workers block ========================

**workers**

Таблица с базовыми данными о сотрудниках.

| name          | a | ky | a | al | type                   |
|:--------------|:-:|:--:|:-:|:--:|:-----------------------|
| id            | A | PK |   |    | increment              |
| name          | R |    |   | RA | char(50)               |
| lastname      | R |    |   | RA | char(50)               |
| partronymic   | R |    |   | RA | char(50)               |
| sex           | R |    | L | RA | char(1)                |
| data_of_birth | R |    |   | RA | date( date )           |
| id_street     | R | FK | P | RA | longint                |
| num_house     | R |    |   | RA | int(0)                 |
| litera_house  |   |    |   | RA | char(1)                |
| num_flat      | R |    |   | RA | int                    |
| post_index    |   |    | M | RA | char( 000000 )         |
| datetime_reg  | A |    |   |    | date( datetime_stamp ) |

---

**workers_otdels**

Таблица-связка между сотрудниками и отделами, в которых они работают.

| name      | a | ky | a | al | type      |
|:----------|:-:|:--:|:-:|:--:|:--------- |
| id        | A | PK |   |    | increment |
| id_worker | R | FK | P | RA | longint   |
| id_otdel  | R | FK | P | RA | longint   |

---

**workers_posts**

Таблица-связка между сотрудниками и их должностями.

| name      | a | ky | a | al | type      |
|:----------|:-:|:--:|:-:|:--:|:----------|
| id        | A | PK |   |    | increment |
| id_worker | R | FK | P | RA | longint   |
| id_post   | R | FK | P | RA | longint   |


## === Data block ========================

**data_accounts**

Таблица, содержащая перечень типов счетов, доступных для открытия клиентами.

| name          | a | ky | a | al | type      |
|:--------------|:-:|:--:|:-:|:--:|:----------|
| id            | A | PK |   |    | increment |
| account_type  | R |    |   | RA | char(20)  |
| description   |   |    |   | RA | text      |
| max_money_sum | R |    |   | RA | money     |

---

**data_cards**

Таблица, содержащая перечень типов банковских карт, доступных для выдачи клиентам.

| name                | a | ky | a | al | type      |
|:--------------------|:-:|:--:|:-:|:--:|:----------|
| id                  | A | PK |   |    | increment |
| card_type           | R |    |   | RA | char(20)  |
| description         |   |    |   | RA | text      |
| max_money_operation | R |    |   | RA | money     |

---

**data_credits**

Таблица, содержащая перечень типов кредитов, доступных для выдачи клиентам.

| name           | a | ky | a | al | type      |
|:---------------|:-:|:--:|:-:|:--:|:----------|
| id             | A | PK |   |    | increment |
| credit_type    | R |    |   | RA | char(40)  |
| description    |   |    |   | RA | text      |
| credit_sum     | R |    |   | RA | money     |
| credit_percent | R |    |   | RA | int       |
| credit_months  | R |    |   | RA | int       |

---

**data_otdels**

Таблица, содержащая перечень типов отделов, в которых могут работать сотрудники.

| name        | a | ky | a | al | type      |
|:------------|:-:|:--:|:-:|:--:|:----------|
| id          | A | PK |   |    | increment |
| otdel       | R |    |   | RA | char(40)  |
| description |   |    |   | RA | text      |
| tasks       |   |    |   | RA | text      |

---

**data_posts**

Таблица, содержащая перечень должностей, доступных сотрудникам.

| name          | a | ky | a | al | type      |
|:--------------|:-:|:--:|:-:|:--:|:----------|
| id            | A | PK |   |    | increment |
| post          | R |    |   | RA | char(60)  |
| description   |   |    |   | RA | text      |
| salary        | R |    |   | RA | money     |
| work_schedule | R |    |   | RA | text      |


## === Geo block ========================

**geo_cities**

Таблица со всеми городами, используемыми в базе данных.

| name       | a | ky | a | al | type      |
|:-----------|:-:|:--:|:-:|:--:|:----------|
| id         | A | PK |   |    | increment |
| id_country | R | FK | P | RA | longint   |
| city       | R |    |   | RA | char(50)  |

---

**geo_countries**

Таблица со всеми странами, используемыми в базе данных.

| name    | a | ky | a | al | type      |
|:--------|:-:|:--:|:-:|:--:|:----------|
| id      | A | PK |   |    | increment |
| country | R | IU |   | RA | char(50)  |

---

**geo_streets**

Таблица со всеми улицами, используемыми в базе данных.

| name    | a | ky | a | al | type      |
|:--------|:-:|:--:|:-:|:--:|:----------|
| id      | A | PK |   |    | increment |
| id_city | R | FK | P | RA | longint   |
| street  | R |    |   | RA | char(50)  |


## === Сoverage block ========================

**coverage_bankomats**

Таблица с данными обо всех подключенных банкоматах.

| name          | a | ky | a | al | type      |
|:--------------|:-:|:--:|:-:|:--:|:----------|
| id            | A | PK |   |    | increment |
| id_department | R | FK | P | RA | longint   |
| balance       | A |    |   | RA | money     |
| is_work       | A |    |   | RA | boolean   |

---

**coverage_departments**

Таблица с данными обо всех отделениях, в которых работают сотрудники.

| name         | a | ky | a | al | type      |
|:-------------|:-:|:--:|:-:|:--:|:----------|
| id           | A | PK |   |    | increment |
| id_street    | R | FK | P | RA | longint   |
| name         | R |    |   | RA | char(50)  |
| num_house    | R |    |   | RA | int       |
| litera_house |   |    |   | RA | char(1)   |

---

**coverage_otdels**

Таблица с данными обо всех отделах, в которых работают сотрудники.

| name          | a | ky | a | al | type      |
|:--------------|:-:|:--:|:-:|:--:|:----------|
| id            | A | PK |   |    | increment |
| id_department | R | FK | P | RA | longint   |
| id_otdel_name | R | FK | P | RA | longint   |
| work_spaces   | A |    |   | RA | int       |
