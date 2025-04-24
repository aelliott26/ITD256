# 3 Queries in Django

## Sequential
- ORM Code

```
Member.objects.filter(last_name__contains="Smith")
```
- SQL Query
```
SELECT "gym_membership_member"."member_id", "gym_membership_member"."first_name", "gym_membership_member"."last_name", "gym_membership_member"."email", "gym_membership_member"."phone_num", "gym_membership_member"."birthday", "gym_membership_member"."m_level" FROM "gym_membership_member" WHERE "gym_membership_member"."last_name" LIKE '%Smith%' LIMIT 21;
```
- Screenshot from pg admin
![Image](./Images/Sequential%20Scan.png)

- This is a sequential scan because the it can't use an index and needs to look through every row to find the rows with the last name smith.
## Index
- ORM Code

```
Member.objects.filter(member_id=12)
```
- SQL Query
```
SELECT "gym_membership_member"."member_id", "gym_membership_member"."first_name", "gym_membership_member"."last_name", "gym_membership_member"."email", "gym_membership_member"."phone_num", "gym_membership_member"."birthday", "gym_membership_member"."m_level"FROM "gym_membership_member" WHERE "gym_membership_member"."member_id" = 12 LIMIT 21;
```
- Screenshot from pg admin
![Image](./Images/Index%20Scan.png)

- This is an index scan because it uses the index to find the member_id that is 12, and can take all of the data from the row, meaning it still needs to use the table to get the entire row.

## Index only
- ORM Code
```
Member.objects.values("member_id").filter(member_id=12)
```
- SQL Query
```
SELECT "gym_membership_member"."member_id" FROM "gym_membership_member" WHERE "gym_membership_member"."member_id" = 12 LIMIT 21;
```
- Screenshot from pg admin
![Image](./Images/Index%20Only%20Scan.png)

- This is an index only scan because the table only uses the data stored in the index meaning it does not need to go to the table at all, making it only use the index.
