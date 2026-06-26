**Topic: Normalization**

1.	Make mutli-valued attributes to single valued 

| Member_Id | First_Name | Last_Name | Hobbies  |
| --------: | ---------- | --------- | -------- |
|       101 | Jayson     | Mark      | Cricket  |
|       101 | Jayson     | Mark      | Swimming |
|       101 | Jayson     | Mark      | Football |
|       102 | Ram        | Ganesh    | Swimming |
|       102 | Ram        | Ganesh    | Running  |
|       102 | Ram        | Ganesh    | Music    |
|       103 | Raj        | Kishore   | Dancing  |
|       103 | Raj        | Kishore   | Singing  |
|       103 | Raj        | Kishore   | Running  |

2.	No Partial Dependency: since {empno, training} is primary key but
Training -> Dept (part of key derives non-key)
**Table 1**

| Empno | Training   | Training_Date |
| ----- | ---------- | ------------- |
| 101   | Oracle SQL | 12-Aug-2015   |
| 101   | Java       | 21-Aug-2015   |
| 102   | Oracle SQL | 18-Sept-2014  |

**Table 2**
| Training   | Dept |
| ---------- | ---- |
| Oracle SQL | TT   |
| Java       | BU   |

3.	{Member_Id} is a PK
Member_Id -> Sports and Sports -> Fees 
KA -> NKA and NKA -> NKA
**Table 1**

| Member_Id | First_Name | Last_Name | Sports   |
| --------- | ---------- | --------- | -------- |
| 101       | Rajesh     | Chand     | Cricket  |
| 102       | Jayesh     | Raj       | Hockey   |
| 103       | Mark       | Dorson    | Football |

**Table 2**

| Sports   | Fees |
| -------- | ---- |
| Cricket  | 100  |
| Hockey   | 80   |
| Football | 90   |




