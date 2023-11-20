# Zadnie 1
```sql
# pkt 1
select * from postac;
select * from postac order by wiek DESC;
select * from postac where rodzaj='wiking' order by wiek DESC;
delete from postac where id_postaci in (8, 9) ;
# pkt 2
SET foreign_key_checks=0;
alter table postac drop primary key;
# problem 1 - atrybut auto increment;
#alter table postac change id_postaci id_postaci int;
# lub przez modify
#krok 1
alter table walizka drop foreign key walizka_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_2;
#krok 2 - pozbycie sie atrybutu auto_increment;
alter table postac modify id_postaci int;
#krok 3 - usunięcie klucza głównego
alter table postac drop primary key;
```
# Zadanie 2
```sql
# pkt 1
alter table postac add pesel char(11) first;
# aktualizacja danych
select * from postac;
update postac set pesel='17763874635' where id_postaci=1;
update postac set pesel='17763874635' + id_postaci;
select * from postac;
# dodanie primary key do tabeli postac
alter table postac add primary key(pesel);

# pkt 2 
alter table postac modify rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena');
#pkt 3
insert into postac values('98765432101',13,'Gertruda Nieszczera','syrena','1642-12-12', 152,null,null); 
```
#Zadanie 3
```sql
update postac set statek='Szybki Sledz'
where nazwa like '%a%';

select * from postac
where nawa like '_j%';

select * from postac where
nazwa regexp '[0-9]{1,2}-[0-9]{3}';
#[0-9] dowolna cyfra ze zbioru
#[adsfg] jeden ze znaków w zbiorze
#określenie rkotności
#{n} co najmniej n razy
#{n,m} conajmniej n razy, nei więcej niż m

insert into statek values('kaprysny karp','duzy', '1974-03-10', 1000);
#pkt 2
#sposob 1
select * from statek
where data_wodowania >= '1901-01-01'
and data_wodowania <= '2000-12-31';
#sposob 2
select * from statek
where data_wodowania between '1901-01-01'
and '2000-12-31';
# tam jest <= >=

#sposob 3
select * from statek
where year(data_wodowania) between 1901 and 2000;
#select hour(now())

update statek set max_ladownosc = 0.7 * max_ladownosc;

#pkt 3

alter table postac
modify wiek int unsigned check (wiek < 1000);
alter table postac add check (wiek < 1000);
#test check
update postac set wiek=1000 where nazwa='Drozd';
```
#zadanie 4
```sql
#pkt 1
select * from postac;
alter table postac modify rodzaj enum('wiking','ptak','kobieta','syrena','waz');
insert into postac values('87654321987',14, 'Loko', 'waz', '1342-10-24', 754,null, null);

#pkt 2

# stworzenie tabeli na wzór innej, bez danych
# z kluczem głównym bez kluczy obcych
create table marynarz like postac;
show create table marynarz;
insert into marynarz select * from postac
where statek is not Null;

#stworzenie tabeli na podstawie zapytania
#select z danymi bez kluczy
create table marynarz2 select id_postaci, nazwa, funkcja, statek from postac;

select * from marynarz;

# pkt 3
alter table marynarz add foreign key (statek) references statek(nazwa_statku);
```
# zadanie 5
```sql
#pkt 1
update postac set statek=null;
select * from postac;
select * from statek;

#pkt 2
delete from postac where nazwa='Erik';

#pkt 3
alter table marynarz drop constraint marynarz_ibfk_1;
alter table postac drop constraint postac_ibfk_1;
delete from statek;

#pkt 4
drop table statek;

#pkt 5
create table zwierz (id_zwierza int primary key auto_increment, nazwa varchar(100), wiek int unsigned);
insert into zwierz(nazwa,wiek) select nazwa,wiek from postac where rodzaj not in('wiking','kobieta');
select * from zwierz;
```
