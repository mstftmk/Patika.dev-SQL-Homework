# Patika.dev-SQL-Homework
Patika.dev Veri Bilimi Patikası SQL ödevleri.

## HW-1
#### Soru-1
* film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
~~~sql
SELECT title, description FROM film;
~~~

#### Soru-2
* film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
~~~sql
SELECT * FROM film
WHERE length > 60 AND length < 75;
~~~

#### Soru-3
* film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
~~~sql
SELECT * FROM film
WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
~~~

#### Soru-4
* customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir? (Cevap: Smith)
~~~sql
SELECT first_name, last_name FROM customer
WHERE first_name = 'Mary';
~~~

#### Soru-5
* film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
~~~sql
SELECT * FROM film
WHERE NOT length > 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);
~~~

## HW-2
#### Soru-1
* film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
~~~sql
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
~~~

#### Soru-2
* .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick', 'Ed');
~~~

#### Soru-3
* film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT * FROM film
WHERE (rental_rate IN (0.99, 2.99, 4,99)) AND (replacement_cost IN (12.99, 15.99, 28.99));
~~~

## HW-3
#### Soru-1
* country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country FROM country
WHERE country LIKE 'A%a';
~~~

#### Soru-2
* country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country FROM country
WHERE country LIKE '_____%n';
~~~

#### Soru-3
* film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
~~~sql
SELECT title FROM film
WHERE title ILIKE '%t%t%t%t%';
~~~

#### Soru-4
* film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
~~~sql
SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;
~~~

## HW-4
#### Soru-1
* film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
~~~sql
SELECT DISTINCT replacement_cost FROM film;
~~~

#### Soru-2
* film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
~~~sql
SELECT COUNT(DISTINCT replacement_cost) FROM film;
~~~

#### Soru-3
* film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
~~~sql
SELECT COUNT(*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
~~~

#### Soru-4
* country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
~~~sql
SELECT COUNT(country) FROM country
WHERE country LIKE '_____';
~~~

#### Soru-5
* city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
~~~sql
SELECT COUNT(*) FROM city
WHERE city ILIKE '%r';
~~~

## HW-5
#### Soru-1
* film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
~~~sql
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
~~~

#### Soru-2
* film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
~~~sql
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length
OFFSET 5
LIMIT 5;
~~~

#### Soru-3
* customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
~~~sql
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
~~~

## HW-6
#### Soru-1
* film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
~~~sql
SELECT AVG(rental_rate) FROM film;
~~~

#### Soru-2
* film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
~~~sql
SELECT COUNT(title) FROM film
WHERE title ILIKE 'C%';
~~~

#### Soru-3
* film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
~~~sql
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
~~~

#### Soru-4
* film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
~~~sql
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;
~~~

## HW-7
#### Soru-1
* film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
~~~sql
SELECT rating FROM film
GROUP BY rating;
~~~

#### Soru-2
* film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
~~~sql
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(replacement_cost) > 50;
~~~

#### Soru-3
* customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
~~~sql
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
~~~

#### Soru-4
* city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
~~~sql
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY country_id DESC
LIMIT 1;
~~~

## HW-8
#### Soru-1
* test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
~~~sql
CREATE TABLE employee(
	id SERIAL PRIMARY KEY,
	name VARCHAR(50) NOT NULL,
	birthday DATE,
	email VARCHAR(100)
);
~~~

#### Soru-2
* Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
~~~sql
insert into employee (name, birthday, email) values ('Phillie Danne', '1901-07-24', 'pdanne0@cloudflare.com');
insert into employee (name, birthday, email) values ('Karry Leadbeater', '1986-04-08', 'kleadbeater1@sphinn.com');
insert into employee (name, birthday, email) values ('Dorolisa Albrook', '1930-01-25', 'dalbrook2@kickstarter.com');
insert into employee (name, birthday, email) values ('Dwayne Sexty', '1918-09-01', 'dsexty3@pagesperso-orange.fr');
insert into employee (name, birthday, email) values ('Godfry Tadgell', '1954-03-29', 'gtadgell4@blogger.com');
insert into employee (name, birthday, email) values ('Brana Loalday', '1917-05-21', 'bloalday5@wikia.com');
insert into employee (name, birthday, email) values ('Israel Nichols', '1945-04-25', 'inichols6@deliciousdays.com');
insert into employee (name, birthday, email) values ('Skipton Snar', '1927-02-27', 'ssnar7@list-manage.com');
insert into employee (name, birthday, email) values ('Mozes Somerfield', '1932-08-07', 'msomerfield8@bluehost.com');
insert into employee (name, birthday, email) values ('Rudolph Aucoate', '1925-06-16', 'raucoate9@123-reg.co.uk');
insert into employee (name, birthday, email) values ('Jayne Sarton', '1936-07-20', 'jsartona@newyorker.com');
insert into employee (name, birthday, email) values ('Osmund Curton', '1992-06-01', 'ocurtonb@domainmarket.com');
insert into employee (name, birthday, email) values ('Michele Polfer', '1980-12-15', 'mpolferc@hatena.ne.jp');
insert into employee (name, birthday, email) values ('Reamonn Safhill', '1996-02-07', 'rsafhilld@dyndns.org');
insert into employee (name, birthday, email) values ('Caritta Twyford', '1971-04-06', 'ctwyforde@scribd.com');
insert into employee (name, birthday, email) values ('Aylmer Sant', '1903-08-14', 'asantf@businessinsider.com');
insert into employee (name, birthday, email) values ('Corine Noirel', '1996-03-15', 'cnoirelg@domainmarket.com');
insert into employee (name, birthday, email) values ('Molli Lyffe', '1917-02-07', 'mlyffeh@deviantart.com');
insert into employee (name, birthday, email) values ('Olive Thowless', '1902-08-06', 'othowlessi@msu.edu');
insert into employee (name, birthday, email) values ('Fallon Clarke-Williams', '1988-01-10', 'fclarkewilliamsj@umn.edu');
insert into employee (name, birthday, email) values ('Salvatore Halladey', '1942-01-24', 'shalladeyk@issuu.com');
insert into employee (name, birthday, email) values ('Jan Easseby', '1948-02-06', 'jeassebyl@mac.com');
insert into employee (name, birthday, email) values ('Sophronia Schonfelder', '1980-06-22', 'sschonfelderm@google.ca');
insert into employee (name, birthday, email) values ('Gregorio McQuillin', '1994-12-31', 'gmcquillinn@techcrunch.com');
insert into employee (name, birthday, email) values ('Angel Jobes', '1955-12-17', 'ajobeso@bravesites.com');
insert into employee (name, birthday, email) values ('Rina MacAndrew', '1970-02-02', 'rmacandrewp@examiner.com');
insert into employee (name, birthday, email) values ('Jilleen Windram', '2006-05-06', 'jwindramq@stumbleupon.com');
insert into employee (name, birthday, email) values ('Sharon Berthod', '1957-02-28', 'sberthodr@pen.io');
insert into employee (name, birthday, email) values ('Sasha Follen', '1938-11-29', 'sfollens@thetimes.co.uk');
insert into employee (name, birthday, email) values ('Lilia Barajas', '2009-09-05', 'lbarajast@unicef.org');
insert into employee (name, birthday, email) values ('Robena Brok', '1984-12-14', 'rbroku@shareasale.com');
insert into employee (name, birthday, email) values ('Natalee Goldsberry', '2008-04-28', 'ngoldsberryv@latimes.com');
insert into employee (name, birthday, email) values ('Tony Samper', '1936-11-01', 'tsamperw@time.com');
insert into employee (name, birthday, email) values ('Fleurette Husher', '1908-07-08', 'fhusherx@nyu.edu');
insert into employee (name, birthday, email) values ('Rochelle Gosenell', '1911-05-02', 'rgosenelly@netscape.com');
insert into employee (name, birthday, email) values ('Shanan Fearnyhough', '1966-03-07', 'sfearnyhoughz@is.gd');
insert into employee (name, birthday, email) values ('Concordia Galer', '1945-03-28', 'cgaler10@huffingtonpost.com');
insert into employee (name, birthday, email) values ('Ruthanne Grafton', '1902-08-08', 'rgrafton11@moonfruit.com');
insert into employee (name, birthday, email) values ('Bev Van der Kruys', '1950-06-24', 'bvan12@yahoo.com');
insert into employee (name, birthday, email) values ('Zara Tamplin', '1976-06-06', 'ztamplin13@who.int');
insert into employee (name, birthday, email) values ('Ashil Gregoli', '1981-11-09', 'agregoli14@issuu.com');
insert into employee (name, birthday, email) values ('Pearl Wyllcock', '1911-09-08', 'pwyllcock15@ox.ac.uk');
insert into employee (name, birthday, email) values ('Harman Dunrige', '1951-10-29', 'hdunrige16@google.cn');
insert into employee (name, birthday, email) values ('Nerty MacGowing', '1900-09-27', 'nmacgowing17@wired.com');
insert into employee (name, birthday, email) values ('Nola McGaw', '1995-06-30', 'nmcgaw18@si.edu');
insert into employee (name, birthday, email) values ('Tess Carbonell', '1975-09-06', 'tcarbonell19@skyrock.com');
insert into employee (name, birthday, email) values ('Marijn Lumpkin', '1972-02-01', 'mlumpkin1a@unblog.fr');
insert into employee (name, birthday, email) values ('Jacquette Blamire', '1903-11-30', 'jblamire1b@mayoclinic.com');
insert into employee (name, birthday, email) values ('Anne-corinne Tysack', '1959-06-10', 'atysack1c@google.com.hk');
insert into employee (name, birthday, email) values ('Karita Richley', '1939-07-14', 'krichley1d@prlog.org');
~~~

#### Soru-3
* Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
~~~sql
UPDATE employee
SET name = 'Angela Jobes'
WHERE email = 'ajobeso@bravesites.com';

UPDATE employee
SET birthday = '1922-08-06'
WHERE name = 'Olive Thowless';

UPDATE employee
SET email = 'barajas@unicef.org'
WHERE id = 30;

UPDATE employee
SET name = 'Pearl Wyllcook',
	birthday = '1935-08-09',
	email = 'pwyllcook@ox.ac.uk'
WHERE id = 42;

UPDATE employee
SET name = 'Oswald Curton',
	email = 'ocurton@domainmarket.com'	
WHERE id = 12;
~~~

#### Soru-4
* Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
~~~sql
DELETE FROM employee
WHERE name = 'Corine Noirel';

DELETE FROM employee
WHERE birthday = '1957-02-28';

DELETE FROM employee
WHERE email = 'rgrafton11@moonfruit.com';

DELETE FROM employee
WHERE id = 14;

DELETE FROM employee
WHERE name = 'Karita Richley' AND birthday = '1939-07-14';
~~~

## HW-9
#### Soru-1
* city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT city, country FROM city
INNER JOIN country ON city.country_id = country.country_id;
~~~

#### Soru-2
* customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT payment_id, first_name, last_name FROM payment
INNER JOIN customer ON payment.customer_id = customer.customer_id;
~~~

#### Soru-3
* customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT rental_id, first_name, last_name FROM rental
INNER JOIN customer ON rental.customer_id = customer.customer_id;
~~~

## HW-10
#### Soru-1
* city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
~~~sql
SELECT city, country FROM city
LEFT JOIN country ON city.country_id = country.country_id;
~~~

#### Soru-2
* customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
~~~sql
SELECT payment_id, first_name, last_name FROM customer
RIGHT JOIN payment ON payment.customer_id = customer.customer_id;
~~~

#### Soru-3
* customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
~~~sql
SELECT rental_id, first_name, last_name FROM customer
FULL JOIN rental ON customer.customer_id = rental.customer_id;
~~~
