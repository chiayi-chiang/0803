# MySQL 資料庫建置與基礎管理

## 2.規畫關聯式資料庫
  - 關聯式資料庫入門概論
    實體與實體會互動
    屬性與屬性不會互動
  - 使用者資料需求分析
  - 資料庫正規化分析
    ＊計算型欄位不佔資料庫空間
    1NF->各屬性皆為單一值屬性，橫向不重複
    2NF->所有屬性都相依於PK，
          直向資料不重複
    3NF->未與pk有直接關連得外建關聯

## MySQL 系統安裝與設定
  - MySQL 系統架構簡介
  - 安裝 MySQL 
  - MySQL 管理工具使用說明
   
## MySQL 基礎系統管理
  - MySQL 身份識別與授權之系統資料表
  - CREATE USER、GRANT、REVOKE 等 DCL 語法
  - 以 MySqlDump 備份資料
  - 資料匯出與匯入

## 3.以 DDL 語法定義資料庫結構
  - CREATE DATABASE
  - CREATE TABLE
  - ALTER TABLE
  - DROP TABLE
  - MySQL 內建資料型別
  - Primary Key 與 Unique
  - Foreign Key
  - CREATE INDEX

## 4.node
  - 關聯customer和order兩表，
    且防止資料其中一方被修改刪除
  create table customer
  (
    cID int auto_increment,
    cName varchar(20)
  ) 
  create table orders
  (
    oID int auto_increment primary key,
    cID int auto_increment
  ) 
  alter table orders
    add constraint fk_customer_orders
      foreign key (customerId) references customer(customerId)
      on update cascade
      on delete cascade;
  - 公司名稱不重複
    alter table customer add constraint uc unique (companyName);
    insert into customer values (4, 'AAA');
    - 去規則
      alter table customer drop constraint uc;
      or
      drop index table customer drop constraint uc;
  - 索引不重複
    create unique index idx_company on customer (companyName);
    insert into customer values(4, 'AAA');
    - 去規則
     drop index idx_company on customer;   
## 1.以 DML 語法存取資料
  - SELECT 查詢排列名稱
  / SELECT Distinct ....不重複資料
  / FROM 從哪個資料表查詢
  / JOIN 連接另一個資料表 on a. ....=b. ...
  /***SELECT X.欄位,Y.欄位
      FROM 欄位 Ｘ JOIN 欄位 Y（比對次數＝左欄位次數）
      ON X. ...ID = Y. ...ID/*兩表PK相*/
  / WHERE 指定哪欄位那些資料
  / ORDER BY 排序,...DESC由大到小,ASC由小到大
  / LIMIT skip,count
  /limit 20,10->需看到第3頁的資料21筆開始->從20開始，每筆出現0～10筆
  / GROUP BY 同資料組群
    /having -二次篩選
    /gollup -多層次統計
  /like 'c%'　以c開頭的字
  /like binary `C%`有大小寫要求
  /... as `....`
  - 子查詢（SubQuery）
  - INSERT  INTO 哪個表（資料欄位１，資料欄位２，資料欄位３，．．．．．）
        value ('','','',....)
  - UPDATE 更改 更新 資料夾
  - DELTE FROM
      WHERE //防止全刪
  －TRUNCATE TABLE //連空間都刪除乾淨
  /WITH ROLLUP
  /union 在欄位數量相等，且資料內容相同，才有連接效果
## 異動（Transaction）與鎖定的觀念與管理
  - 異動（Transaction）的 ACID 特性
  - 理解 Transaction Isolation Level 與上機實驗
  - SELECT ... LOCK IN SHARE MORE
  - SELECT ... FOR UPDATE
  convert(...,varchar)//轉換字串

