# MySQL 資料庫建置與基礎管理

## 規畫關聯式資料庫
  - 關聯式資料庫入門概論
  - 使用者資料需求分析
  - 資料庫正規化分析

## MySQL 系統安裝與設定
  - MySQL 系統架構簡介
  - 安裝 MySQL 
  - MySQL 管理工具使用說明
   
## MySQL 基礎系統管理
  - MySQL 身份識別與授權之系統資料表
  - CREATE USER、GRANT、REVOKE 等 DCL 語法
  - 以 MySqlDump 備份資料
  - 資料匯出與匯入

## 以 DDL 語法定義資料庫結構
  - CREATE DATABASE
  - CREATE TABLE
  - ALTER TABLE
  - DROP TABLE
  - MySQL 內建資料型別
  - Primary Key 與 Unique
  - Foreign Key
  - CREATE INDEX

## 以 DML 語法存取資料
  - SELECT 查詢排列名稱
  / SELECT Distinct ....不重複資料
  / FROM 從哪個資料表查詢
  / JOIN 連接另一個資料表 on a. ....=b. ...
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
  - INSERT
  - UPDATE
  - DELTE

## 異動（Transaction）與鎖定的觀念與管理
  - 異動（Transaction）的 ACID 特性
  - 理解 Transaction Isolation Level 與上機實驗
  - SELECT ... LOCK IN SHARE MORE
  - SELECT ... FOR UPDATE
  convert(...,varchar)//轉換字串