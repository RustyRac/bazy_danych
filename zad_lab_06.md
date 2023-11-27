# Zadanie 1
```sql
#1
create table kreatura As(select * from wikingowie.kreatura);
create table zasob As(select * from wikingowie.zasob);
create table ekwipunek As(select * from wikingowie.ekwipunek);
#2
select * from zasob;
#3
select * from zasob where rodzaj='jedzenie';
#4
select nazwa from kreatura where idKreatury in (1, 3, 5);
```

# Zadanie 2
```sql
# 1
select * from kreatura where
udzwig >= 50 and rodzaj != 'wiedzma';
# 2
select * from zasob where waga >= 2 and waga <= 5;
# 3
select * from kreatura where nazwa like '%or%' and udzwig >= 30 and udzwig <= 70;
```

# Zadanie 3
```sql
#1
dataPozyskania regexp '[0-9]{4}-[0]{1}[7-8]{1}-[0-9]{2}';
#lub z month
select * from zasob where month(dataPozyskania) in (7,8);
#2
select * from zasob order by waga asc;
#3
select * from kreatura order by dataUr desc limit 5;
```

# Zadanie 4
```sql
#1
select distinct rodzaj from zasob;
#2
select concat(nazwa,' - ', rodzaj) from kreatura where rodzaj like 'wi%';
#3
select nazwa,ilosc*waga as waga_calkowita from zasob where year(dataPozyskania)<=2007 and year(dataPozyskania)>=2000;
```

# Zadanie 5
```sql
#1
select nazwa,waga,waga*0.3 as masa_odpadku from zasob where rodzaj = 'jedzenie';
#2
select * from zasob where rodzaj is null;
#3
select distinct rodzaj from zasob where nazwa like 'Ba%' or nazwa like '%os' order by rodzaj asc; 
```

