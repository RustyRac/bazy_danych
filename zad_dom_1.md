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
Zadanie 3
```sql
create table izba( adres_budynku varchar(40), nazwa_izby varchar(40),
primary key(adres_budynku, nazwa_izby),
metraz int unsigned,
id_wlasciciela int,
foreign key (id_wlasciciela) references postac(id_postaci) on delete set null);

ALTER TABLE izba ADD [COLUMN] kolor_izby enum("rozowy","zolty","bialy") AFTER metraz;

insert into izba values("Chatka Bjorna","Spizarnia", 20, "bialy", 1);
```
Zadanie 4
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

