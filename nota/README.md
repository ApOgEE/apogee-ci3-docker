## Nota MySQL

```

select *, REPLACE(trim(ic),'-','') from persons where ic is not null and INSTR(ic,'-') > 0 limit 100;

select *, REPLACE(REPLACE(trim(ic),'-',''),' ','') from persons where ic is not null and INSTR(ic,'-') > 0 limit 100;

select * from persons where ic is not null limit 100;

UPDATE persons SET ic = REPLACE(REPLACE(trim(ic),'-',''),' ','') WHERE ic IS NOT NULL AND INSTR(ic,'-') > 0;

DELETE persons, address, bank_accounts, emails, phones FROM persons INNER JOIN address ON address.person_id = persons.person_id INNER JOIN bank_accounts ON bank_accounts.person_id = persons.person_id INNER JOIN emails ON emails.person_id = persons.person_id INNER JOIN phones ON phones.person_id = persons.person_id WHERE persons.person_id = 1242;

SELECT * FROM persons
INNER JOIN address ON address.person_id = persons.person_id
WHERE persons.person_id = 1242;


SELECT a.agent_id, a.agent_no, a.active_status, a.refer_id, p.person_id, p.name, p.ic FROM agents AS a INNER JOIN persons as p ON p.person_id = a.person_id WHERE a.refer_id = 0;


SELECT refer_id, count(refer_id) FROM agents GROUP BY refer_id HAVING count(refer_id) > 1;

# cari duplicate
SELECT distinct a.refer_id, a.person_id, a.agent_no FROM agents a, agents b WHERE a.refer_id = b.refer_id AND a.person_id != b.person_id;

SELECT distinct a.refer_id, a.person_id, a.agent_no FROM agents a, agents b WHERE a.agent_no = b.agent_no AND a.person_id != b.person_id;

SELECT a.agent_id, a.person_id, p.name, p.ic FROM agents a INNER JOIN persons p ON p.person_id = a.person_id  WHERE a.agent_no = 0;

```