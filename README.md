# PatikaDev-PostgreSQL
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
## Ödev 3
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
SELECT country From Country WHERE country like 'A%a';
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
SELECT country From Country WHERE LENGTH(country) > 6 AND country like '%n';
#### Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren
SELECT title FROM film WHERE title ILIKE '%t%t%t%t%';
#### Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
SELECT * From film Where title LIKE 'C%' AND length > 90 AND rental_rate = 2.99 ; 

## Ödev 4
#### Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
SELECT DISTINCT replacement_cost FROM film; 
#### Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
SELECT COUNT( DISTINCT replacement_cost ) FROM film; 
#### Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
SELECT COUNT(*) FROM film WHERE title = 'T%' AND rating = 'G';
#### Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
SELECT COUNT(*) FROM film WHERE LENGTH(country) = 5;
#### City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
SELECT COUNT(*) FROM City WHERE ILIKE city = '%R';



# PSQL ve Uygulama I
## PSQL
### PSQL, PostgreSQL ile birlikte gelen terminal tabanlı bir kullanıcı arayüzüdür. PSQL sayesinde komut satırında sorgular yazıp, sonuçlarını görebiliriz. Aşağıda temel PSQL komutlarının ilk bölümünü bulabilirsiniz.

#### PSQL ile PostgreSQL'e bağlanmak.
~~~
psql -U <kullanıcı_adı>
~~~
#### Kullanıcıya ait şifreyi girdikten sonra varsayılan veritabanı postgres'e bağlanıyor.
~~~
postgres=#
~~~
#### Bulunan veritabanlarını listelemek için:
~~~
\l veya \list
~~~
#### Bizim örneğimizde dvdrental veritabanına bağlanacağız.
~~~
\c dvdrental veya \connect dvdrental
~~~
#### Bağlanılan dvdrental veritabanında bulunan tabloları listelemek için:
~~~
\dt
~~~
#### Herhangi bir tablonun sütunlarını ve tablo detaylarını görmek için:
~~~
\dt <tablo_adı>
~~~
#### PSQL terminal ekranından çıkmak için:
~~~
\q
~~~

#### Örnek Sorgu Senaryoları
#### Customer tablosunda bulunan first_name değeri ve last_name değeri 'A' karakteri ile başlayan verileri sıralayınız.
~~~
SELECT * 
FROM customer
WHERE first_name LIKE 'A%' AND last_name LIKE 'A%';
~~~
#### Film tablosunda bulunan ve uzunluğu 80 ile 120 arasında bulunan ve aynı zamanda rental_rate değeri 0.99 veya 2.99 olan verileri sıralayınız.
~~~
SELECT * 
FROM film
WHERE (length BETWEEN 80 AND 120) AND (rental_rate IN (0.99, 2.99));
~~~


# NOTLAR
### ~~ = LIKE ,  ~~ * = ILIKE , !~~ = NOT LIKE ,  !~~ * = NOT LIKE

