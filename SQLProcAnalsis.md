# growth

-- checking inconsistancies between start_date and ended_at
SELECT rented, month
FROM year
WHERE rented<0

-----
-- rented is less 0
DELETE
FROM
year
where rented<0 

------

--creating table mem_month and mem_rented in min
SELECT
month,round(sum(rented)/60) as mem_rented, sum(member_casual= "member") as mem_user
FROM
year
WHERE member_casual = "member"
group by month

--creating table tot_month
-- tot_rented in min
SELECT
month,round(sum(rented)/60) as tot_rented, sum(member_casual= "member_casual") as tot_user
FROM
year
group by month

-----
--creating table cas_month and cas_rented in min
SELECT
month,round(sum(rented)/60) as cas_rented, sum(member_casual= "casual") as cas_user
FROM
year
WHERE member_casual = "casual"
group by month

---------

-- joining cas_month to mem_month to cas_mem_month
SELECT cas_month.month, cas_rented, mem_rented, cas_user, mem_user
FROM
cas_month JOIN mem_month on cas_month.month = mem_month.month

-----

-- joining cas_month to mem_month to month
-- rented in min
SELECT cas_mem_month.month, cas_rented, mem_rented, tot_rented, cas_user, mem_user,tot_user
FROM
cas_mem_month JOIN tot_month on cas_mem_month.month = tot_month.month

-------

-- joining cas_month to mem_month to cas_mem_month
SELECT cas_month.month, cas_rented, mem_rented, cas_user, mem_user
FROM
cas_month JOIN mem_month on cas_month.month = mem_month.month

------


