import sqlite3 as db

#con = db.connect('noma.db')

#con.close



with db.connect('noma.db') as con:
    cur = con.cursor
    cur = con.execute(""" CREATE TABLE IF NOT EXISTS Noma (
	id_produkts	INTEGER NOT NULL,
	id_nomnieks	INTEGER NOT NULL,
	sak_datums TEXT,
	beig_datums	TEXT,
	PRIMARY KEY(id_produkts,id_nomnieks)
)
                      """)

with db.connect('kategorija.db') as con:
    cur = con.cursor
    cur = con.execute(""" CREATE TABLE IF NOT EXISTS Kategorija (
	id_kategorija	INTEGER NOT NULL UNIQUE,
	kategorija	TEXT,
	PRIMARY KEY(id_kategorija AUTOINCREMENT)
)
                      """)

with db.connect('nomnieks.db') as con:
    cur = con.cursor
    cur = con.execute(""" CREATE TABLE IF NOT EXISTS Nomnieks (
	id_nomnieks	INTEGER NOT NULL UNIQUE,
	vards	TEXT,
	uzvards	TEXT,
	p_k_	INTEGER,
	tel_nr	INTEGER,
	PRIMARY KEY(id_nomnieks AUTOINCREMENT)
)
                      """)

with db.connect('nosaukums.db') as con:
    cur = con.cursor
    cur = con.execute(""" CREATE TABLE IF NOT EXISTS Nosaukums (
	id_nosaukums	INTEGER NOT NULL UNIQUE,
	nosaukums	TEXT,
	PRIMARY KEY(id_nosaukums AUTOINCREMENT)
)
                      """)

with db.connect('tehn_raksturojums.db') as con:
    cur = con.cursor
    cur = con.execute(""" CREATE TABLE IF NOT EXISTS Tehn_raksturojums (
	id_tehn_raksturojums	INTEGER NOT NULL UNIQUE,
	tehnikas_raksturojums	TEXT,
	PRIMARY KEY(id_tehn_raksturojums AUTOINCREMENT)
)
                      """)

with db.connect('produkts.db') as con:
    cur = con.cursor
    cur = con.execute(""" CREATE TABLE IF NOT EXISTS Produkts (
	id_produkts	INTEGER NOT NULL UNIQUE,
	id_kategorija	TEXT,
	id_nosaukums	TEXT,
	id_tehn_raksturojums	TEXT,
	nomas_cena_diena	REAL,
	PRIMARY KEY(id_produkts AUTOINCREMENT)
)
                      """)
