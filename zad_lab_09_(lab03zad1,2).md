# Zadania 1 
```sql
# zad 1
select imie, nazwisko, data_urodzenia from __firma_zti.pracownik;

# zad 2

select imie, nazwisko, year(curdate())- year(data_urodzenia) as wiek from __firma_zti.pracownik;

# zad 3

select d.nazwa, count(distinct p.id_pracownika) as "liczba pracowników" from __firma_zti.dzial d
left join __firma_zti.pracownik p on p.dzial = d.id_dzialu
group by d.nazwa;

# zad 4

select k.nazwa_kategori, count(t.id_towaru) as ilosc from __firma_zti.towar t
inner join __firma_zti.kategoria k on t.kategoria = k.id_kategori
group by k.id_kategori;

# zad 5

select k.nazwa_kategori, group_concat(t.nazwa_towaru) from __firma_zti.towar t
inner join __firma_zti.kategoria k on t.kategoria = k.id_kategori
group by k.id_kategori;

# zad 6

select round(avg(pensja), 2) from __firma_zti.pracownik;

# zad 7

select round(avg(pensja), 2) from __firma_zti.pracownik
where year(curdate()) - year(data_zatrudnienia) >= 5;

# zad 8

select t.nazwa_towaru, sum(pz.ilosc) from __firma_zti.towar t
inner join __firma_zti.pozycja_zamowienia pz
on t.id_towaru=pz.towar
group by t.nazwa_towaru
order by 2 DESC limit 10;

# zad 9

select z.numer_zamowienia, sum(pz.ilosc * pz.cena) from __firma_zti.zamowienie z
inner join __firma_zti.pozycja_zamowienia pz on z.id_zamowienia=pz.zamowienie
where year(z.data_zamowienia) = 2017 and quarter(z.data_zamowienia) = 1
group by z.id_zamowienia;

# zad 10

select p.imie, p.nazwisko, sum(pz.ilosc* pz.cena) as wartosc from __firma_zti.zamowienie z
inner join __firma_zti.pozycja_zamowienia pz on z.id_zamowienia=pz.zamowienie
inner join __firma_zti.pracownik p on p.id_pracownika=z.pracownik_id_pracownika
group by p.id_pracownika
order by wartosc desc;
```
# Zadania 2

```sql

# zad 1 

select d.nazwa, min(p.pensja), max(p.pensja), avg(p.pensja) from__firma_zti.pracownik p
inner join __firma_zti.dzial d on p.dzial=d.id_dzialu
group by d.id_dzialu;

# zad 2

select k.pelna_nazwa, sum(pz.ilosc * pz.cena) as wartosc from __firma_zti.zamowienie z
inner join __firma_zti.pozycja_zamowienia pz on z.id_zamowienia=pz.zamowienie
inner join __firma_zti.klient k on k.id_klienta=z.klient
group by z.id_zamowienia
order by wartosc desc limit 10;

# zad 3

select sum(pz.cena * pz.ilosc) as przychod, year(z.data_zamowienia) as rok from __firma_zti.pozycja_zamowienia pz
inner join __firma_zti.zamowienie z on pz.zamowienie=z.id_zamowienia
group by year(z.data_zamowienia)
order by przychod desc;

# zad 7

select sum(pz.cena * pz.ilosc - t.cena_zakupu * pz.ilosc) as "dochód", year(z.data_zamowienia) from __firma_zti.pozycja_zamowienia pz
inner join __firma_zti.zamowienie z on pz.zamowienie=z.id_zamowienia
inner join __firma_zti.towar t on pz.towar= t.id_towaru
group by year(z.data_zamowienia);












```

