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

**clients_telefons**

- id
- id_client
- tel_num

**clients_accounts**

- id
- id_client
- type
- number
- balance

**clients_passports**

- id
- id_client
- pass_


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
- name
- description
- work_spaces

**coverage_bankomats**

- id
- id_department
- balance
- is_work




# Что есть?

* клиенты
	- счета
	- карты
	- вклады
	- кредиты
	- переводы
		- внутри банка
		- внешние банки
	- траты
	- начисления

* сотрудники
	- должность
	- отдел
	- подчинённые сотрудники

* информация
	- курсы валют
	- предоставляемые услуги
	- денежные потоки

* отделения
	- позиция
	- сотрудники
	- банкоматы
