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
```
