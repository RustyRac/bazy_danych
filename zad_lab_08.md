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
# Zadanie 2
```sql
# pkt 1
select rodzaj, group_concat(nazwa separator ' ')
from kreatura group by rodzaj;

select * from uczestnicy;

select w.nazwa, count(distinct k.nazwa) as LiczbaUczestnikow, group_concat(k.nazwa separator ', ') as BioracyUdzial from kreatura k 
inner join uczestnicy u on k.idKreatury = u.id_uczestnika
inner join wyprawa w on w.id_wyprawy = u.id_wyprawy
group by w.nazwa;

# pkt 2

select * from kreatura;
select * from etapy_wyprawy;
select * from wyprawa;
select * from sektor;

select w.nazwa, e.dziennik, s.nazwa, k.nazwa from wyprawy w
left join ;
```

# zad 3
```sql
# pkt 3

select k.nazwa, count(u.id_wyprawy) from kreatura k
left join uczestnicy u on u.id_uczestnika=k.idKreatury
group by k.nazwa;

# pkt 2

select s.id_sektora, if(count(ew.sektor) = 0, 'Nie brał udziału w wyprawie', 'Brał udział w wyprawie') as czy_wyprawa
from etapy_wyprawy ew
right join sektor s on ew.sektor=s.id_sektora
group by s.id_sektora;
```

# zad 4

```sql
# pkt 1
select rodzaj, group_concat(nazwa separator ' ')
from kreatura group by rodzaj;

select * from uczestnicy;

select w.nazwa, count(distinct k.nazwa) as LiczbaUczestnikow, group_concat(k.nazwa separator ', ') as BioracyUdzial from kreatura k 
inner join uczestnicy u on k.idKreatury = u.id_uczestnika
inner join wyprawa w on w.id_wyprawy = u.id_wyprawy
group by w.nazwa;

# pkt 2

select * from kreatura;
select * from etapy_wyprawy;
select * from wyprawa;
select * from sektor;

select w.nazwa, e.dziennik, s.nazwa, k.nazwa from wyprawy w
left join ;
```
# zad 5

```sql
select k.nazwa, datediff(w.data_rozpoczecia,k.dataUr) as 'Wiek w dniach' from kreatura k
inner join uczestnicy u on u.id_uczestnika=k.idKreatury
inner join etapy_wyprawy ew on u.id_wyprawy=ew.idWyprawy
inner join wyprawa w on w.id_wyprawy=u.id_wyprawy
where ew.sektor=7;
```
