CREATE TABLE user (
userId TEXT NOT NULL PRIMARY KEY,
password TEXT NOT NULL,
userType TEXT NOT NULL);

INSERT INTO user VALUES ('11111','rahasiadong','admin');
INSERT INTO user VALUES ('22222','apaajaboleh','user');
INSERT INTO user VALUES ('33333','lupalagi','user');
INSERT INTO user VALUES ('44444','tidaktau','user');
INSERT INTO user VALUES ('55555','1sampai9','user');

CREATE TABLE customer (
customerId INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
userId TEXT NOT NULL,
name TEXT NOT NULL,
address TEXT NOT NULL,
phoneNumber TEXT NOT NULL,
email TEXT NOT NULL,
sex TEXT NOT NULL,
billingAddress TEXT NOT NULL,
FOREIGN KEY(userId) REFERENCES user(userId));

INSERT INTO customer VALUES (null,'11111','Eki Fakhrureza','Ciganitri','087874957002','ekifakhrureza@gmail.com','L','Ciganitri');
INSERT INTO customer VALUES (null,'22222','Agung Prabowo','Margacinta','087364674232','agungp@gmail.com','L','Margacinta');
INSERT INTO customer VALUES (null,'33333','Ahmad Yusuf','Kiaracondong','089997376363','yusuf@gmail.com','L','Kiaracondong');
INSERT INTO customer VALUES (null,'44444','Putra Janitra','Jatinangor','086363535344','putra@gmail.com','L','Jatinangor');
INSERT INTO customer VALUES (null,'55555','Fitri Ramadhani','Panghegar','087773633','fitri@gmail.com','P','Panghegar');


CREATE TABLE transactionTbl(
transactionId TEXT NOT NULL PRIMARY KEY,
userId TEXT NOT NULL,
transactionDate TEXT NOT NULL,
paymentMethod TEXT NOT NULL,
paymentStatus TEXT NOT NULL,
deliveryStatus TEXT NOT NULL,
FOREIGN KEY(userId) REFERENCES user(userId));

INSERT INTO transactionTbl VALUES ('trans-001','11111','2017-12-01 09:09:09','Bank Transfer','Paid','Delivered');
INSERT INTO transactionTbl VALUES ('trans-002','22222','2017-10-21 10:10:55','Bank Transfer','Paid','Delivered');
INSERT INTO transactionTbl VALUES ('trans-003','33333','2017-09-09 06:18:07','Bank Transfer','Paid','Delivered');
INSERT INTO transactionTbl VALUES ('trans-004','44444','2017-09-09 05:07:06','Bank Transfer','Paid','Delivered');
INSERT INTO transactionTbl VALUES ('trans-005','55555','2017-09-09 11:22:33','Bank Transfer','Paid','Delivered');

CREATE TABLE transactionProduct(
transactionProductId INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
productId TEXT NOT NULL,
transactionId TEXT NOT NULL,
quantity INTEGER NOT NULL,
FOREIGN KEY(productId) REFERENCES product(productId),
FOREIGN KEY(transactionId) REFERENCES transactionTbl(transactionId));

INSERT INTO transactionProduct VALUES(null,'BG-001','trans-001',2);
INSERT INTO transactionProduct VALUES(null,'BG-002','trans-002',1);
INSERT INTO transactionProduct VALUES(null,'BG-003','trans-003',1);
INSERT INTO transactionProduct VALUES(null,'BG-003','trans-004',1);
INSERT INTO transactionProduct VALUES(null,'BG-004','trans-005',2);

CREATE TABLE product(
productId TEXT NOT NULL PRIMARY KEY,
name TEXT NOT NULL,
price TEXT NOT NULL,
cloth TEXT NOT NULL,
size TEXT NOT NULL,
color TEXT NOT NULL,
stock INTEGER NOT NULL);

INSERT INTO product VALUES('BG-001','tas gawl','100000','cotton','small','merah',10);
INSERT INTO product VALUES('BG-002','tas gokz','150000','kulit','medium','kuning',5);
INSERT INTO product VALUES('BG-003','tas ntpz','200000','suede','small','hijau',20);
INSERT INTO product VALUES('BG-004','tas nais','300000','satin','big','merah',14);
INSERT INTO product VALUES('BG-005','tas skoy','500000','cotton','medium','hitam',2);


CREATE TABLE productTag(
productTagId INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
productId TEXT NOT NULL,
tagId INTEGER NOT NULL,
FOREIGN KEY(productId) REFERENCES product(productId),
FOREIGN KEY(tagId) REFERENCES tag(tagId));

INSERT INTO productTag VALUES(null,'BG-001',4);
INSERT INTO productTag VALUES(null,'BG-002',1);
INSERT INTO productTag VALUES(null,'BG-002',5);
INSERT INTO productTag VALUES(null,'BG-003',2);
INSERT INTO productTag VALUES(null,'BG-003',3);

CREATE TABLE tag(
tagId INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
tagName TEXT NOT NULL);

INSERT INTO tag VALUES(null,'kulit');
INSERT INTO tag VALUES(null,'suede');
INSERT INTO tag VALUES(null,'satin');
INSERT INTO tag VALUES(null,'small');
INSERT INTO tag VALUES(null,'medium');
