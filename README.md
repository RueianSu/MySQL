# MySQL筆記

## 基礎指令

### 顯示所有資料庫
顯示所有資料庫，會顯示目前有的表單。


```sql=
show databases;
```
---
### 新增資料庫`database`

透過`create`方式指定為`database`型態，民稱叫做`first`

```sql=
create database first;
```
---
### :sos: 刪除資料庫`database` ==危險操作==

透過 `drop` 方式指定為`database`型態，民稱叫做`first`，把他刪除。


```sql=
drop database first;
```

:::danger
:hand: !!!!!特別注意不可還原，上班基本上用不到，使用到會被開除，危險操作。
:::

---

### 前往指定資料庫`use`

透過`use`前往叫做`first`資料庫
```sql=
use first;
```

---

### 檢視目前在哪裡

```sql=
select database();
```

---

### 新建`table`

新建一個 `employee` 的表單，其中裡面包含employee_id、employee_name、employee_age.... ，資料名稱與型態。
```sql=
create table employee(
employee_id int,
employee_name varchar(50),
employee_age int,
employee_salary bigint,
employee_department varchar(50)
);
```

----

### `desc`檢視新建表單內容
透過`desc`查看表格設定

```sql=
desc employee;
```

---

### :sos: `drop`刪除表格 ==危險操作==


```sql=
drop table employee;
```

:::danger
:hand: !!!!!特別注意不可還原，上班基本上用不到，使用到會被開除，危險操作。
:::

### SQL資料型態

參考 : https://ithelp.ithome.com.tw/articles/10203456

---

### 新建資料到`table`

1. 查看目前位置
```sql=
select databases();
```
2. 前往`first`
```sql=
use first;
```
3. 查看表單設定
```sql=
show columns from employee;
```
4. 新建資料
```sql=
insert into employee(
    employee_id,
    employee_name,
    employee_age,
    employee_salary,
    employee_department
) values(1,'a',2,3,'aa');
```

5. 查詢是否新建成功
```sql=
select * from employee;
```

6. 查看屬性
```sql=
desc first_nation;
```

全部程式碼

```sql=
select database();/* 查看目前位置*/

use first;/*前往first*/

show columns from employee;/*查看表單設定*/


insert into employee(
    employee_id,
    employee_name,
    employee_age,
    employee_salary,
    employee_department
) values(1,'a',2,3,'aa');/*新建資料*/

select * from employee;/*查詢 employee 是否建立資料成功*/

desc first_nation;/*查看屬性*/

```

:::info


### 錯誤訊息解決方式

![image](https://hackmd.io/_uploads/B1--LSg1A.png)


解決方式

1.關閉ide

2.開啟工作管理員

3.啟動服務
![image](https://hackmd.io/_uploads/HkXcUreJ0.png)


:::

---

### 表單建立常用指令功能

#### 組建 `primary key`

1. 主要功能 ==避免產生一堆重複又無法識別的編號==
2. `primary key`一定要是唯一的，不可以重複

---

#### `auto_increment`自動新增號碼



1. 加上後會配合`primary key`自動加一

---

#### `not null` 不能是空直

1. 加上後表單==一定要輸入數值==不然有錯

#### `nsert into` 表單名稱(數據資料)

透過`nsert into`  新增表單資料，例如:


```sql=
insert into first_nation value(null,'Albania',28748,2831741,12960000000)
```
:::info
補充:
1. 如果是 `primary key auto_increment`輸入 `null`會制動判斷變數是否要加1。

2. 如果是順序相同`first_nation`與` value`中間可以不指定變數型態，否則需要像下面方式輸入:
```sql=
insert into first_nation(id,name,area,population,gdp)value(
3,'Albania',28748,2831741,12960000000)
```
:::

#### 範例 



```sql=
select database(); /*查看現在在哪*/
create database nation; /*新建數據庫*/

use nation;/*前往數據庫*/
select database(); /*查看現在在哪*/

/*新建表格*/
create table first_nation(
id int not null primary key auto_increment,
name varchar(60) not null,
area int not null,
population int not null ,
gdp bigint not null
);

/*看屬性*/
desc first_nation;

/*看資料*/
select * from first_nation;
/*加新資料*/
insert into first_nation value(null,'Albania',28748,2831741,12960000000);

/*看資料*/
select * from first_nation;
```
