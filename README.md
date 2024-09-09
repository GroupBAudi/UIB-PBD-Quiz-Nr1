# UIB-PBD-Quiz1

Q1

```mysql
CREATE TABLE BOOK
(	Book_id int VARCHAR(255),
	Title VARCHAR(255),
	Publisher_name VARCHAR(255),
	PRIMARY KEY (Book_id),
	CONSTRAINT Fk_publisher_name FOREIGN KEY (Publisher_name) REFERENCES PUBLISHER(Name)
		ON UPDATE CASCADE
		ON DELETE CASCADE
);

CREATE TABLE BOOK_AUTHORS
(
 	Author_name VARCHAR(255),
  	Book_id int VARCHAR(255),
  	PRIMARY KEY (Book_id, Author_name),
  	CONSTRAINT Fk_book_id FOREIGN KEY (Book_id) REFERENCES BOOK(Book_id)
	  	ON UPDATE CASCADE
	  	ON DELETE CASCADE
);

CREATE TABLE PUBLISHER
(
 	Name VARCHAR(255),
  	Address VARCHAR(255),
  	Phone VARCHAR(255),
	PRIMARY KEY (Name)
);

CREATE TABLE BOOK_COPIES
(
 	Book_id int VARCHAR(255),
  	Branch_id int VARCHAR(255),
  	No_of_copies int VARCHAR(255),
  	PRIMARY KEY (Book_id, Branch_id),
  	CONSTRAINT Fk_book_id FOREIGN KEY (Book_id) REFERENCES BOOK(Book_id),
  	CONSTRAINT Fk_branch_id FOREIGN KEY (Branch_id) REFERENCES LIBRARY_BRANCH(Branch_id)
		ON UPDATE CASCADE
		ON DELETE CASCADE
);

CREATE TABLE BOOK_LOANS
(
	Book_id int VARCHAR(255),
  	Branch_id int VARCHAR(255),
  	Card_no int VARCHAR(255),
  	Date_out DATE,
	Due_date DATE,
	PRIMARY KEY (Book_id, Branch_id, Card_no),
  	CONSTRAINT Fk_book_id FOREIGN KEY (Book_id) REFERENCES BOOK(Book_id),
  	CONSTRAINT Fk_branch_id FOREIGN KEY (Branch_id) REFERENCES LIBRARY_BRANCH(Branch_id),
  	CONSTRAINT Fk_card_no FOREIGN KEY (Card_no) REFERENCES BORROWER(Card_no)
	  	ON UPDATE CASCADE
	  	ON DELETE CASCADE
);

CREATE TABLE LIBRARY_BRANCH
(
	Branch_id int VARCHAR(255),
  	Branch_name VARCHAR(255),
  	Address VARCHAR(255),
  	PRIMARY KEY (Branch_id)
);

CREATE TABLE BORROWER
(
 	Card_no int VARCHAR(255),
  	Name VARCHAR(255),
  	Address VARCHAR(255),
  	Phone VARCHAR(255),
  	PRIMARY KEY (Card_no)
);
```

Q2

```mysql
CREATE TABLE BOOK
(	Book_id int VARCHAR(255),
	Title VARCHAR(255),
	Publisher_name VARCHAR(255),
	PRIMARY KEY (Book_id),
	CONSTRAINT Fk_publisher_name FOREIGN KEY (Publisher_name) REFERENCES PUBLISHER(Name)
		ON UPDATE CASCADE
		ON DELETE CASCADE
);

CREATE TABLE BOOK_AUTHORS
(
 	Author_name VARCHAR(255),
  	Book_id int VARCHAR(255),
  	PRIMARY KEY (Book_id, Author_name),
  	CONSTRAINT Fk_book_id FOREIGN KEY (Book_id) REFERENCES BOOK(Book_id)
	  	ON UPDATE CASCADE
	  	ON DELETE CASCADE
);

CREATE TABLE PUBLISHER
(
 	Name VARCHAR(255),
  	Address VARCHAR(255),
  	Phone VARCHAR(255),
	PRIMARY KEY (Name)
);

CREATE TABLE BOOK_COPIES
(
 	Book_id int VARCHAR(255),
  	Branch_id int VARCHAR(255),
  	No_of_copies int VARCHAR(255),
  	PRIMARY KEY (Book_id, Branch_id),
  	CONSTRAINT Fk_book_id FOREIGN KEY (Book_id) REFERENCES BOOK(Book_id),
  	CONSTRAINT Fk_branch_id FOREIGN KEY (Branch_id) REFERENCES LIBRARY_BRANCH(Branch_id)
		ON UPDATE CASCADE
		ON DELETE CASCADE
);

CREATE TABLE BOOK_LOANS
(
	Book_id int VARCHAR(255),
  	Branch_id int VARCHAR(255),
  	Card_no int VARCHAR(255),
  	Date_out DATE,
	Due_date DATE,
	PRIMARY KEY (Book_id, Branch_id, Card_no),
  	CONSTRAINT Fk_book_id FOREIGN KEY (Book_id) REFERENCES BOOK(Book_id),
  	CONSTRAINT Fk_branch_id FOREIGN KEY (Branch_id) REFERENCES LIBRARY_BRANCH(Branch_id),
  	CONSTRAINT Fk_card_no FOREIGN KEY (Card_no) REFERENCES BORROWER(Card_no)
	  	ON UPDATE CASCADE
	  	ON DELETE CASCADE
);

CREATE TABLE LIBRARY_BRANCH
(
	Branch_id int VARCHAR(255),
  	Branch_name VARCHAR(255),
  	Address VARCHAR(255),
  	PRIMARY KEY (Branch_id)
);

CREATE TABLE BORROWER
(
 	Card_no int VARCHAR(255),
  	Name VARCHAR(255),
  	Address VARCHAR(255),
  	Phone VARCHAR(255),
  	PRIMARY KEY (Card_no)
);

INSERT INTO BORROWER
VALUES(1, "Alan", "123, Yum Street, TX", 1234);

INSERT INTO BORROWER
VALUES(2, "Belen", "456, Yuck Street, FL", 4321);

INSERT INTO BORROWER
VALUES(3, "Evelyn", "789, Normal Street, DE", 1123);

INSERT INTO BORROWER
VALUES(4, "Kazuma", "112, Japantown, GA", 1233);

INSERT INTO BORROWER
VALUES(5, "Dennis", "321, Whichstreet, WA", 4341);

INSERT INTO LIBRARY_BRANCH
VALUES("B001", "Perpustakaan Cabang Batam Center", "Kompleks The Summer A-03");

INSERT INTO LIBRARY_BRANCH
VALUES("B002", "Perpustakaan Cabang Lubuk Baja", "Kompleks Ruko Inti Sakti Blok A No.90");

INSERT INTO PUBLISHER
VALUES('Pearson', '9 N Buona Vista Dr, 13-05/06 The Metropolis Tower One, Singapore 138588', '+65 6319 9388');

INSERT INTO BOOK
VALUES('BO216', 'Fundamental of Database Systems', 'Pearson');

INSERT INTO BOOK_AUTHORS
VALUES
('Ramez Elmasri', 'BO216'),
('Shamkant B. Navathe', 'BO216');

INSERT INTO BOOK_COPIES
VALUES('BO216', 'B001', 3);

ALTER TABLE BOOK_LOANS
ADD Status;

ALTER TABLE BOOK_LOANS
ADD Date_Returned;

INSERT INTO BOOK_LOANS
VALUES('BO216', 'B001', 1, '2024-09-09', '2024-09-31', 'Returned', '2024-09-01')
```

