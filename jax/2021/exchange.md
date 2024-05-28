Select, um die Daten aus der Host-Datenbank zu extrahieren:

select MMART as art, pruef_wert as pruefwert,  bisbetr as bis_betrag, mmwhrg as merkmal_bis_betrag, hinweistext as hinweistext, case stp when '0' then 'false' else 'true' end as stp_wert, BED_ERF as creation_user, ZEITPUNKT_ERF as creation_time, user_update as USER_UPDATE, time_update as TIME_UPDATE,ZEITPUNKT_LAEND as modification_time,
'' as activation_time,'' as dialog_lock_time, '' as dialog_lock_user,BED_LAEND as  modification_user from di0ad009.vizprmm1 where gatyp in ('A','Z')  

Aufbau der Tabelle:

NAME

	

TYPE

	

IS_NULLABLE

	

Beschreibung




id

	BIGINT	NO	Technische ID


art

	Decimal(3)	NO	Art
pruefwert	VARCHAR(35)	NO	

bis_betrag	Decimal(23,5)	NO	

merkmal_bis_betrag	Char(1)	NO	

hinweistext	VARCHAR(70)	NO	

stp_wert	boolean	NO	

creation_user	VARCHAR (10)	NO	

creation_time	TIMESTAMP	NO	

user_update	VARCHAR (10)	NO	

time_update	TIMESTAMP	NO	

activation_time	TIMESTAMP	YES	

dialog_lock_time	TIMESTAMP	YES	

dialog_lock_user	VARCHAR (10)	YES	

modification_time	TIMESTAMP	NO	

modification_user	VARCHAR (10)	NO	



