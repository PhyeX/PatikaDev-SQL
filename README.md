# PatikaDev-SQL
## Ödev 1
#### Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
SELECT title,description FROM film;
#### Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
SELECT * FROM film WHERE length > 60 and length < 75;
#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
SELECT * FROm film WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 29.99
#### Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
SELECT last_name FROM customer where first_name = 'Mary';
Cevap : Smith
#### Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
SELECT * FROM film WHERE  length < 50 AND  NOT rental_RATE = 2.99 OR NOT rental_rate = 4.99
## Ödev 2
#### Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
SELECT * FROM film WHERE BETWEEN 12.99 AND 16.99
#### Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
SELECT first_name,last_name FROM Actor WHERE first_name IN('Penelope','Nick','Ed');

#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.(IN operatörünü kullanınız.)
SELECT * FROM film WHERE rental_rate IN(0.99,2,99,4,99) AND replacement_cost IN(12,99,15,99,28,99);



