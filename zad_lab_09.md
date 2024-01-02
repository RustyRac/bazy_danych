# lab 09

```sql
select * from kreatura;
delete from kreatura where nazwa='Amigo';
# 

DELIMITER //
CREATE TRIGGER kreatura_before_insert
BEFORE INSERT ON kreatura
FOR EACH ROW
BEGIN
  IF NEW.waga <= 0
  THEN
    SET NEW.waga = 1;
 END IF;
END
//

insert into kreatura values(50, 'Amigo','wiking', '1671-04-04', 0, 59);

# zad 2

select w.id_wyprawy, w.nazwa ,w.data_rozpoczecia, w.data_zakonczenia, k.nazwa from wyprawa w
inner join kreatura k on k.idKreatury=w.kierownik
where id_wyprawy=1;

DELIMITER $$
create trigger wyprawa_after_delete
after delete on wyprawa
for each row
begin
insert into archiwum_wyprawy values(
select w.id_wyprawy, w.nazwa ,w.data_rozpoczecia, w.data_zakonczenia, k.nazwa from wyprawa w
inner join kreatura k on k.idKreatury=w.kierownik
where id_wyprawy=old.id_wyprawy;

end
$$
```
