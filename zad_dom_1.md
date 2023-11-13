# Zadanie 1
```sql
create table postac ( id_postaci int primary key auto_increment, nazwa varchar(40) not null,
rodzaj enum('wiking', 'ptak', 'kobieta'), data_ur date, wiek int unsigned);

insert into postac values (default,"Bjorn","wiking","1700-10-23",23);

insert into postac values(default,"Drozd","ptak","1540-10-23",234);

insert into postac values(default,"Tesciowa","kobieta","1-01-01",234);

update postac set wiek=88 where id_postaci=5;
```
# Zadanie 2
```sql
create table walizka(id_walizki int primary key auto_increment, pojemnosc int unasigned,
kolor enum("rozowy", "czerwony", "teczowy", "zolty"), id_wlasciciela int,
foreign key (id_wlasciciela) references postac(id_postaci) on delete cascade);

alter table walizka alter kolor set default "rozowy";

insert into walizka values(default,100,"zolty",1);
```
# Zadanie 3
```sql
create table izba( adres_budynku varchar(40), nazwa_izby varchar(40),
primary key(adres_budynku, nazwa_izby),
metraz int unsigned,
id_wlasciciela int,
foreign key (id_wlasciciela) references postac(id_postaci) on delete set null);

ALTER TABLE izba ADD COLUMN kolor_izby enum("rozowy","zolty","bialy") AFTER metraz;

insert into izba values("Chatka Bjorna","Spizarnia", 20, "bialy", 1);
```
# Zadanie 4
```sql
create table przetwory( id_przetworu int primary key, 
rok_produkcji int default "1654", 
id_wykonawcy int, foreign key (id_wykonawcy) references postac(id_postaci), 
zawartosc varchar(40), 
dodatek varchar (40) default "papryczka chilli", 
id_konsumenta int, 
foreign key (id_konsumenta) references postac(id_postaci);

insert into przetwory values(1,1700, 1, "bigos",default, 5);
```
# Zadanie 5
```sql
select * from postac;
# pkt 1
INSERT INTO postac values
(default, 'Asgard', 'wiking', '1678-06-12', 320),
(default, 'Rupert', 'wiking', '1678-11-12', 344),
(default, 'Greg', 'wiking', '1678-02-12', 240),
(default, 'Erik', 'wiking', '1678-05-12', 312),
(default, 'Halfdan', 'wiking', '1678-03-12', 124);
select * from postac;
# pkt 2
create table statek ( nazwa_statku varchar(50) primary key,
rodzaj_statku enum('maly', 'sredni', 'duzy'),
data_wodowania date,
max_ladownosc int unsigned);
# pkt 6
ALTER TABLE postac ADD COLUMN statek varchar(50) default null;
ALTER TABLE postac ADD FOREIGN KEY (statek) references
statek(nazwa_statku) on delete set null;
# pkt 3
INSERT INTO statek values
('szybki sledz', 'duzy', '1524-06-12', 452),
('dorodny dorsz', 'sredni', '1124-04-12', 312);
# pkt 4
select * from postac;
ALTER TABLE postac ADD COLUMN funkcja varchar(50) AFTER wiek;
select * from postac;
# pkt 5
update postac set funkcja='kapitan' where id_postaci=1;
select * from postac;
# pkt 7
update postac set statek='szybki sledz' where id_postaci in (1,3,9,10,12);
update postac set statek='dorodny dorsz' where id_postaci in (8,11);
select * from postac;
# pkt 8
select * from izba;
delete from izba where nazwa_izby='Spizarnia';
# pkt 9
drop table izba;
```

