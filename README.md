# hg
select start_date,min(end_date) from
(select start_date from projects where start_date not in (select end_date from projects)) as a,
(select end_date from projects where end_date not in (select start_date from projects))as b
where start_date< end_date
group by start_date
order by DATEDIFF(MIN(end_date), start_date), start_date;
