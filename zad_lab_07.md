# zadanie 1
```sql
#1

select waga from kreatura;
#suma
select sum(waga) from kreatura;
#ilość wystąpień (ignoruje null)
select count(waga) from kreatura;
#średnia wystąpień (ignoruje null)
select avg(waga) from kreatura;


select avg(waga) from kreatura where rodzaj='wiking';

#2

select avg(waga), count(rodzaj) from kreatura group by rodzaj;

#3

select rodzaj, avg(2023 - year(dataUr)) as wiek from kreatura group by rodzaj;

```

# zadanie 2
```sql
#1

select rodzaj,sum(waga * ilosc) from zasob group by rodzaj;

#2

select nazwa, avg(waga) from zasob where ilosc >= 4 group by nazwa having sum(waga);

#3
select count(distinct nazwa) from zasob group by rodzaj having min(ilosc) > 1;
```

# zadanie 3
```sql
#1
select k.nazwa, k.idKreatury, e.idKreatury from kreatura k, ekwipunek e
where k.idKreatury = e.idKreatury;

select k.nazwa, e.ilosc from kreatura k, ekwipunek e
where k.idKreatury = e.idKreatury;
#2

select k.nazwa, z.nazwa from kreatura k
inner join ekwipunek e on k.idKreatury = e.idKreatury
inner join zasob z on z.idZasobu = e.idZasobu; 

#3

select k.idKreatury, e.idKreatury from kreatura k
left join ekwipunek e on k.idKreatury = e.idKreatury
where e.idKreatury is null;

select distinct idKreatury from ekwipunek;

select idKreatury from kreatura
where idKreatury not in 
(select idKreatury from ekwipunek where idKreatury is not null);

```

# zadanie 4
```sql
#1
select * from kreatura
natural join ekwipunek;

#2

```
