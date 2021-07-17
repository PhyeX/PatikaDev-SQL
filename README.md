# PatikaDev-PostgreSQL

<a href='#Ödev 1'>Ödev 1</a><br>
<a href='#Ödev 2'>Ödev 2</a><br>
<a href='#Ödev 3'>Ödev 3</a><br>
<a href='#Ödev 4'>Ödev 4</a><br>
<a href='#Ödev 5'>Ödev 5</a><br>
<a href='#Ödev 6'>Ödev 6</a><br>
<a href='#Ödev 7'>Ödev 7</a><br>
<a href='#Ödev 8'>Ödev 8</a><br>
<a href='#Ödev 9'>Ödev 9</a><br>
<a href='#Ödev 10'>Ödev 10</a><br>
<a href='#Ödev 11'>Ödev 11</a><br>
<a href='#Ödev 12'>Ödev 12</a><br>
<a href='#psql'>PSQL ve Uygulama </a><br>
<a href='#Notlar'>Notlar </a><br>
 
 
 
## <p id = 'Ödev 1' > Ödev 1 </p> 
#### Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
~~~sql
SELECT title,description FROM film;
~~~
#### Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
~~~sql
SELECT * FROM film WHERE length > 60 and length < 75;
~~~
#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
~~~sql
SELECT * FROm film WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99
~~~
#### Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
~~~sql
SELECT last_name FROM customer where first_name = 'Mary';
Cevap : Smith
~~~
#### Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
~~~sql
SELECT * FROM film WHERE  length < 50 AND  NOT rental_RATE = 2.99 OR NOT rental_rate = 4.99
~~~
## <p id = 'Ödev 2' > Ödev 2 </p> 
#### Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
~~~sql
SELECT * FROM film WHERE BETWEEN 12.99 AND 16.99
~~~
#### Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT first_name,last_name FROM Actor WHERE first_name IN('Penelope','Nick','Ed');
~~~
#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.(IN operatörünü kullanınız.)
~~~sql
SELECT * FROM film WHERE rental_rate IN(0.99,2,99,4,99) AND replacement_cost IN(12.99,15.99,28.99);
~~~
## <p id = 'Ödev 3' > Ödev 3 </p> 
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country From Country WHERE country like 'A%a';
~~~
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country From Country WHERE LENGTH(country) > 6 AND country like '%n';
~~~
#### Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren
~~~sql
SELECT title FROM film WHERE title ILIKE '%t%t%t%t%';
~~~
#### Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
~~~sql
SELECT * From film Where title LIKE 'C%' AND length > 90 AND rental_rate = 2.99 ; 
~~~

## <p id = 'Ödev 4' > Ödev 4 </p> 
#### Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
~~~sql
SELECT DISTINCT replacement_cost FROM film; 
~~~
#### Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
~~~sql
SELECT COUNT( DISTINCT replacement_cost ) FROM film; 
~~~
#### Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
~~~sql
SELECT COUNT(*) FROM film WHERE title = 'T%' AND rating = 'G';
~~~
#### Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
~~~sql
SELECT COUNT(*) FROM film WHERE LENGTH(country) = 5;
~~~
#### City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
~~~sql
SELECT COUNT(*) FROM City WHERE ILIKE city = '%R';
~~~


## <p id = 'Ödev 5' > Ödev 5 </p> 
#### Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
~~~sql
SELECT title FROM film WHERE title LIKE '%n' LIMIT 5;
~~~
#### Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
~~~sql
SELECT title FROM film WHERE title LIKE '%n' OFFSET 5 LIMIT 5;
~~~
#### Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
~~~sql
SELECT last_name FROM customer WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;
~~~

## <p id = 'Ödev 6' > Ödev 6 </p> 
#### Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
~~~sql
SELECT AVG(rental_rate) FROM film;
~~~
#### Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
~~~sql
SELECT COUNT(*) FROM film WHERE title LIKE 'C%';
~~~
#### Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
~~~sql
SELECT MAX(length) FROM film WHERE rental_rate = 0.99;
~~~
#### Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
~~~sql
SELECT COUNT( DISTINCT replacement_cost )FROM film WHERE length > 150;
~~~
## <p id = 'Ödev 7' > Ödev 7 </p> 
#### Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
~~~sql
SELECT rating FROM film GROUP BY rating;
~~~
#### Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
~~~sql
SELECT replacement_cost,COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*) > 50;
~~~
#### Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
~~~sql
SELECT store_id,COUNT(*) FROM customer GROUP BY store_id;
~~~
#### City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
~~~sql
SELECT country_id,COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;
~~~
## <p id = 'Ödev 8' > Ödev 8 </p>
#### Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
~~~sql
 CREATE TABLE employee (
  id SERIAL PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(100),
  birthday DATE
);
~~~
#### Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
~~~sql
insert into Employee (id, name, email, birthday) values (1, 'Barth', 'bpoulston0@gizmodo.com', '2020/12/15');
insert into Employee (id, name, email, birthday) values (2, 'Elysia', 'earter1@shutterfly.com', '2020/11/22');
insert into Employee (id, name, email, birthday) values (3, 'Averill', 'astithe2@weibo.com', '2020/09/05');
insert into Employee (id, name, email, birthday) values (4, 'Edgardo', 'etomsett3@eepurl.com', '2021/02/17');
insert into Employee (id, name, email, birthday) values (5, 'Jan', 'jmoreno4@newsvine.com', '2020/11/11');
insert into Employee (id, name, email, birthday) values (6, 'Ethelbert', 'ebatrop5@boston.com', '2020/11/18');
insert into Employee (id, name, email, birthday) values (7, 'Heda', 'hchartre6@g.co', '2021/05/01');
insert into Employee (id, name, email, birthday) values (8, 'Thornie', 'ttorres7@feedburner.com', '2020/11/11');
insert into Employee (id, name, email, birthday) values (9, 'Jeffry', 'jcohane8@chicagotribune.com', '2021/07/07');
insert into Employee (id, name, email, birthday) values (10, 'Aaron', 'agossipin9@1und1.de', '2020/08/23');
insert into Employee (id, name, email, birthday) values (11, 'Pauly', 'pweldona@nydailynews.com', '2020/10/07');
insert into Employee (id, name, email, birthday) values (12, 'Feodora', 'fsemourb@nbcnews.com', '2020/12/09');
insert into Employee (id, name, email, birthday) values (13, 'Corey', 'ccardoec@engadget.com', '2021/06/04');
insert into Employee (id, name, email, birthday) values (14, 'Kellina', 'knorthcoted@behance.net', '2020/09/06');
insert into Employee (id, name, email, birthday) values (15, 'Suzi', 'spracye@tuttocitta.it', '2020/09/08');
insert into Employee (id, name, email, birthday) values (16, 'Karylin', 'ksommerlandf@buzzfeed.com', '2021/05/12');
insert into Employee (id, name, email, birthday) values (17, 'Lindsy', 'lfanningg@xinhuanet.com', '2021/05/06');
insert into Employee (id, name, email, birthday) values (18, 'Jaquenette', 'jpechah@independent.co.uk', '2021/01/25');
insert into Employee (id, name, email, birthday) values (19, 'Arda', 'amacmillani@census.gov', '2020/08/31');
insert into Employee (id, name, email, birthday) values (20, 'Zea', 'zmostinj@engadget.com', '2020/07/14');
insert into Employee (id, name, email, birthday) values (21, 'Gilligan', 'groskellyk@disqus.com', '2021/07/07');
insert into Employee (id, name, email, birthday) values (22, 'Derward', 'dbraybrookesl@chronoengine.com', '2021/02/21');
insert into Employee (id, name, email, birthday) values (23, 'Garrik', 'gfilipicm@geocities.jp', '2020/12/14');
insert into Employee (id, name, email, birthday) values (24, 'Michelle', 'mstoddn@fc2.com', '2020/11/15');
insert into Employee (id, name, email, birthday) values (25, 'Margaux', 'mrableno@fema.gov', '2021/04/05');
insert into Employee (id, name, email, birthday) values (26, 'Kyle', 'kmeconip@stanford.edu', '2021/03/29');
insert into Employee (id, name, email, birthday) values (27, 'Kelcie', 'khuishq@umich.edu', '2021/02/11');
insert into Employee (id, name, email, birthday) values (28, 'Suzy', 'sstairmandr@google.com.br', '2020/08/27');
insert into Employee (id, name, email, birthday) values (29, 'Benedict', 'bgyteshams@cornell.edu', '2020/09/27');
insert into Employee (id, name, email, birthday) values (30, 'Haleigh', 'htollet@ca.gov', '2021/07/05');
insert into Employee (id, name, email, birthday) values (31, 'Lilith', 'lnorthallu@auda.org.au', '2021/02/08');
insert into Employee (id, name, email, birthday) values (32, 'Simone', 'sshoebrookv@aboutads.info', '2021/02/23');
insert into Employee (id, name, email, birthday) values (33, 'Pietrek', 'pharewoodw@intel.com', '2020/10/19');
insert into Employee (id, name, email, birthday) values (34, 'Issi', 'ielpheex@hc360.com', '2021/07/04');
insert into Employee (id, name, email, birthday) values (35, 'Alisa', 'agollyy@lulu.com', '2020/09/02');
insert into Employee (id, name, email, birthday) values (36, 'Reynard', 'rdubblez@examiner.com', '2021/04/10');
insert into Employee (id, name, email, birthday) values (37, 'Maurine', 'mgurley10@nih.gov', '2020/11/03');
insert into Employee (id, name, email, birthday) values (38, 'Malcolm', 'mluard11@cnet.com', '2020/07/10');
insert into Employee (id, name, email, birthday) values (39, 'Konstantine', 'khowsan12@spiegel.de', '2021/02/18');
insert into Employee (id, name, email, birthday) values (40, 'Mady', 'mscopyn13@adobe.com', '2021/05/02');
insert into Employee (id, name, email, birthday) values (41, 'Nowell', 'nilden14@berkeley.edu', '2021/01/13');
insert into Employee (id, name, email, birthday) values (42, 'Toiboid', 'tlinnit15@naver.com', '2021/01/06');
insert into Employee (id, name, email, birthday) values (43, 'Russ', 'rburdus16@github.com', '2021/02/07');
insert into Employee (id, name, email, birthday) values (44, 'Celeste', 'cniblo17@cafepress.com', '2021/01/18');
insert into Employee (id, name, email, birthday) values (45, 'Prentiss', 'phabercham18@vimeo.com', '2021/02/09');
insert into Employee (id, name, email, birthday) values (46, 'Adelle', 'aharrold19@sohu.com', '2020/09/02');
insert into Employee (id, name, email, birthday) values (47, 'Ebba', 'elemonnier1a@indiatimes.com', '2020/11/12');
insert into Employee (id, name, email, birthday) values (48, 'Valina', 'vgallandre1b@t.co', '2021/01/04');
insert into Employee (id, name, email, birthday) values (49, 'Teena', 'tkitchingham1c@jigsy.com', '2021/05/29');
insert into Employee (id, name, email, birthday) values (50, 'Shel', 'scrone1d@hud.gov', '2021/02/11');
~~~

#### Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
~~~sql
UPDATE Employee SET name = 'Barbaros' WHERE id = 1;
UPDATE Employee SET email = 'rtb.barbaros@gmail.com' WHERE name = 'Barbaros';
UPDATE Employee SET birthday = '2021/05/29' WHERE email = '123@gmail.com';
UPDATE Employee SET birthday = '2021/05/29',name = 'Revaha' WHERE email = '123@gmail.com';
UPDATE Employee SET name = 'Barbaros',birthday = '2021/05/29' WHERE id = 1;
~~~
#### Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
~~~sql
DELETE FROM Employee WHERE name = 'Revaha';
DELETE FROM Employee WHERE email = 'rtb.barbaros@gmail.com';
DELETE FROM Employee WHERE birthday = '2021/05/29';
DELETE FROM Employee WHERE name = 'Tayyip';
DELETE FROM Employee WHERE id = '1';
~~~
## <p id = 'Ödev 9' > Ödev 9 </p> 
#### City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT city,country FROM city ci JOIN country co ON (co.country_id = ci.country_id );
~~~
#### Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT first_name,last_name,payment_id FROM customer c JOIN payment p ON ( p.customer_id = c.customer_id);
~~~
#### Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT first_name,last_name,rental_id FROM customer c JOIN rental r ON( c.customer_id = r.customer_id );
~~~
##  <p id = 'Ödev 10' > Ödev 10 </p> 
#### City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
~~~sql
SELECT city,country FROM city ci LEFT JOIN country co ON ( ci.country_id = co.country_id );
~~~
#### Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
~~~sql
SELECT first_name,last_name,payment_id FROM customer c RIGHT JOIN payment p ON ( p.customer_id = c.customer_id);
~~~
#### Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
~~~sql
SELECT first_name,last_name,rental_id FROM customer c FULL JOIN rental r ON( c.customer_id = r.customer_id );
~~~

##  <p id = 'Ödev 11' > Ödev 11 </p> 
#### Actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
~~~sql
( SELECT first_name FROM actor )
UNION
( SELECT first_name FROM customer )
~~~
#### Actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
~~~sql
( SELECT first_name FROM actor )
INTERSECT
( SELECT first_name FROM customer )
~~~
#### Actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
~~~sql
( SELECT first_name FROM actor )
EXCEPT
( SELECT first_name FROM customer )
~~~
#### İlk 3 sorguyu tekrar eden veriler için de yapalım.
~~~sql
( SELECT first_name FROM actor )
UNION ALL
( SELECT first_name FROM customer )
~~~
~~~sql
( SELECT first_name FROM actor )
INTERSECT ALL
( SELECT first_name FROM customer )
~~~
~~~sql
( SELECT first_name FROM actor )
EXCEPT ALL
( SELECT first_name FROM customer )
~~~
## <p id = 'Ödev 12' > Ödev 12 </p>
#### Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
~~~sql
SELECT COUNT(*)  FROM film WHERE length > ( SELECT AVG(length) FROM film);
~~~
#### Film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
~~~sql
SELECT COUNT(*) FROM film WHERE rental_rate = ( SELECT MAX(rental_rate) FROM film);
~~~
#### Film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
~~~sql
SELECT title
FROM film
WHERE film_id = any
( SELECT film_id
 FROM film
WHERE rental_rate = ( SELECT MIN(rental_rate ) FROM film )
 AND
 replacement_cost = ( SELECT MIN(replacement_cost) FROM film ) );
~~~
#### Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
~~~sql
SELECT first_name,last_name
FROM customer c
JOIN payment p
ON ( p.customer_id = c.customer_id )
WHERE amount = ( SELECT MAX(amount) from payment );
~~~


# <p id = 'psql1' > PSQL ve Uygulama I </p> 
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
~~~sql
\dt <tablo_adı>
~~~
#### PSQL terminal ekranından çıkmak için:
~~~
\q
~~~
#### PSQL ile PostgreSQL'e host, port, kullanıcı adı ve veritabanı ismi ile bağlanmak için:
~~~sql
psql -h <host_name> -p <port_name> -U <kullanıcı_adı> <veritabanı_adı>
~~~
#### Yeni veritabanı oluşturmak için
~~~sql
CREATE DATABASE <veritabanı_adı>
~~~
#### Yeni tablo oluşturmak için
~~~sql
CREATE TABLE <tablo_adı> {
  <sütun_adı> VERİ TİPİ (KISITLAMA)
  <sütun_adı> VERİ TİPİ (KISITLAMA)
  ...}
 ~~~
#### Tablo detaylarını görmek için
~~~sql
\d+ <tablo_adı>
~~~
#### Bir tablodaki sütun ismini değiştirmek için
~~~sql
ALTER TABLE <tablo_adı> RENAME COLUMN <sütun_adı> TO <yeni_sütun_adı>
~~~
#### Bir sütuna UNIQUE kısıtlaması eklemek için
~~~sql
ALTER TABLE <tablo_adı> ADD CONSTRAINT <kısıtlama_adı> UNIQUE <sütun_adı>
~~~

#### Örnek Sorgu Senaryoları
#### Customer tablosunda bulunan first_name değeri ve last_name değeri 'A' karakteri ile başlayan verileri sıralayınız.
~~~sql
SELECT * 
FROM customer
WHERE first_name LIKE 'A%' AND last_name LIKE 'A%';
~~~
#### Film tablosunda bulunan ve uzunluğu 80 ile 120 arasında bulunan ve aynı zamanda rental_rate değeri 0.99 veya 2.99 olan verileri sıralayınız.
~~~sql
SELECT * 
FROM film
WHERE (length BETWEEN 80 AND 120) AND (rental_rate IN (0.99, 2.99));
~~~

# <p id = 'Notlar' > NOTLAR </p> 
~~~sql
 ~~ = LIKE ,  ~~* = ILIKE , !~~ = NOT LIKE ,  !~~* = NOT LIKE
~~~

