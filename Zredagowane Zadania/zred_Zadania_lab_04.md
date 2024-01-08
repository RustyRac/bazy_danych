# zad 1
### pkt 1
```sql
create table postac ( id_postaci int primary key auto_increment, nazwa varchar(40) not null,
rodzaj enum('wiking', 'ptak', 'kobieta'), data_ur date, wiek int unsigned);
select * from postac;
```
### pkt 2
```sql
insert into postac values (default,"Bjorn","wiking","1700-10-23",23);

insert into postac values(default,"Drozd","ptak","1540-10-23",234);

insert into postac values(default,"Tesciowa","kobieta","1-01-01",234);
```
### pkt 3
```sql
update postac set wiek=88 where id_postaci=3;
```
# zad 2
### pkt 1
```sql
create table walizka(id_walizki int primary key auto_increment,
 pojemnosc int unsigned,
kolor enum("rozowy", "czerwony", "teczowy", "zolty"),
 id_wlasciciela int,
 foreign key (id_wlasciciela) references postac(id_postaci) on delete cascade);
 ```
 ### pkt 2
 ```sql
 alter table walizka alter kolor set default "rozowy";
 ```
 ### pkt 3
 ```sql
 insert into walizka values(default,100,"zolty",1);
 insert into walizka values(default,120,default,3);
 
 select * from walizka;
 ```
 # zad 3
 ### pkt 1
 ```sql
 create table izba(adres_budynku varchar(40),
 nazwa_izby varchar(40),
primary key(adres_budynku, nazwa_izby),
metraz int unsigned,
id_wlasciciela int,
foreign key (id_wlasciciela) references postac(id_postaci) on delete set null);
```
### pkt 2
 ```sql
 ALTER TABLE izba ADD COLUMN kolor_izby enum("czarny", "rozowy","zolty","bialy") default "czarny" AFTER metraz;
 ```
### pkt 3
 ```sql
 insert into izba values("Chatka Bjorna","Spizarnia", 20, default, 1);
 
 select * from izba;
 ```
# zad 4
### pkt 1
```sql
create table przetwory( id_przetworu int primary key, 
rok_produkcji int default "1654", 
id_wykonawcy int, foreign key (id_wykonawcy) references postac(id_postaci), 
zawartosc varchar(40), 
dodatek varchar (40) default "papryczka chilli", 
id_konsumenta int, 
foreign key (id_konsumenta) references postac(id_postaci));
```
### pkt 2
```sql
insert into przetwory values(1,1700, 1, "bigos",default, 3);
select * from przetwory;
 ```
# zad 5
### pkt 1
```sql
INSERT INTO postac values
(default, 'Asgard', 'wiking', '1678-06-12', 320),
(default, 'Rupert', 'wiking', '1678-11-12', 344),
(default, 'Greg', 'wiking', '1678-02-12', 240),
(default, 'Erik', 'wiking', '1678-05-12', 312),
(default, 'Halfdan', 'wiking', '1678-03-12', 124);
select * from postac;
 ```
### pkt 2
```sql
create table statek ( nazwa_statku varchar(50) primary key,
rodzaj_statku enum('maly', 'sredni', 'duzy'),
data_wodowania date,
max_ladownosc int unsigned);
```
### pkt 3
```sql
INSERT INTO statek values
('szybki sledz', 'duzy', '1524-06-12', 452),
('dorodny dorsz', 'sredni', '1124-04-12', 312);
```
### pkt 4
```sql
select * from postac;
ALTER TABLE postac ADD COLUMN funkcja varchar(50) AFTER wiek;
select * from postac;
```
### pkt 5
```sql
update postac set funkcja='kapitan' where id_postaci=1;
select * from postac;
```
### pkt 6
```sql
ALTER TABLE postac ADD COLUMN statek varchar(50) default null;
ALTER TABLE postac ADD FOREIGN KEY (statek) references
statek(nazwa_statku) on delete set null;
```
### pkt 7
```sql
update postac set statek='szybki sledz' where id_postaci in (1,2,4,7,8);
update postac set statek='dorodny dorsz' where id_postaci in (5,6);
select * from postac;
```
### pkt 8
```sql
select * from izba;
delete from izba where id_wlasciciela=1;
```
### pkt 9
```sql
drop table izba;
```
