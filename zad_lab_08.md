# Zadanie 1
```sql
#pkt 1
select rodzaj,
group_concat(nazwa separator ' i '), count(*)
from kreatura group by rodzaj;

create table uczestnicy As(select * from wikingowie.uczestnicy);
create table etapy_wyprawy As(select * from wikingowie.etapy_wyprawy);
create table sektor As(select * from wikingowie.sektor);
create table wyprawa As(select * from wikingowie.wyprawa);
#pkt 2

select * from wyprawa;
select * from uczestnicy;
select * from etapy_wyprawy;
select * from sektor;
select * from kreatura;

select * from uczestnicy u
inner join kreatura k on k.idKreatury = u.id_uczestnika;

select nazwa from kreatura k
where k.idKreatury not in (select k.idKreatury from uczestnicy u
inner join kreatura k on k.idKreatury = u.id_uczestnika);

#pkt 3

select w.nazwa, sum(e.ilosc) from wyprawa w
inner join uczestnicy u on u.id_wyprawy = w.id_wyprawy
inner join kreatura k on k.idKreatury = u.id_uczestnika
inner join ekwipunek e on k.idKreatury = e.idKreatury
group by w.nazwa;

```
