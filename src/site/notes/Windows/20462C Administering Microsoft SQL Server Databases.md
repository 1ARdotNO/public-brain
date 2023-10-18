---
{"dg-publish":true,"permalink":"/windows/20462-c-administering-microsoft-sql-server-databases/","tags":["public","kurs","mssql"],"noteIcon":"1","created":"2023-08-15T14:20:12.000+02:00","updated":"2023-10-18T10:11:38.785+02:00"}
---

# Backup

#### full backup

backup **database** mandag **to** disk = 'R:\\Backups\\mandagfull.bak'  
**with** init

#### til backup device

backup **database** mandag **to** mandagfulldevice

#### diff backup

backup **database** mandag **to** disk = 'R:\\Backups\\mandagdiff.bak'  
**with** differential, init

#### log backup

backup log mandag **to** disk = 'R:\\Backups\\mandagdlog.trn'  
  
**with** init

#### log tail backup

backup log mandag **to** disk = 'R:\\Backups\\mandagdlogTail.trn'  
**with** no\_truncate, init

#### backup med compression

backup **database** mandag **to** disk = 'R:\\Backups\\mandagfullcomp.bak'  
**with** init, compression

#### backup til fler filer

backup **database** mandag **to** disk = 'R:\\Backups\\mandagfullA.bak'  
,disk = 'R:\\Backups\\mandagfullB.bak'

#### backup til fler filer v2

backup **database** mandag **to** disk = 'R:\\Backups\\mandagfullA2.bak'  
mirror **to** disk = 'R:\\Backups\\mandagfullB2.bak'  
**with** format

#### info om backup-filer

restore headeronly **from** disk = 'R:\\Backups\\mandagfull.bak'  
  
restore labelonly **from** disk = 'R:\\Backups\\mandagfull.bak'  
  
restore verifyonly **from** disk = 'R:\\Backups\\mandagfull.bak'  
  
restore filelistonly **from** disk = 'R:\\Backups\\mandagfull.bak'

#### restore full+diff+log

\--close existing connections  
  
**alter** **database** mandag **set** single\_user **with** **rollback** **immediate**  
  
\--log tail backup  
  
backup log mandag **to** disk = 'R:\\Backups\\mandagdlogTail.trn'  
**with** no\_truncate, init  
  
\--full  
  
restore **database** mandag **from** disk = 'R:\\Backups\\mandagfull.bak'  
**with** norecovery ---- ,replace --> uten tail  
  
\--diff  
  
restore **database** mandag **from** disk = 'R:\\Backups\\mandagdiff.bak'  
**with** norecovery  
  
\--log  
  
restore log mandag **from** disk = 'R:\\Backups\\mandagdlog.trn'  
**with** norecovery  
  
\--tail  
  
restore log mandag **from** disk = 'R:\\Backups\\mandagdlogTail.trn'  
**with** recovery

#### ut av single user

**alter** **database** mandag **set** multi\_user

#### ut av restore modus

restore **database** mandag **with** recovery

#### restore to point in time

USE \[master\]  
**ALTER** **DATABASE** \[Mandag\] **SET** SINGLE\_USER **WITH** **ROLLBACK** **IMMEDIATE**  
RESTORE **DATABASE** \[Mandag\] **FROM** DISK = 'R:\\Backups\\mandagfull.bak'  
**WITH** FILE = 1, NORECOVERY, NOUNLOAD, STATS = 5  
RESTORE LOG \[Mandag\] **FROM** DISK = 'R:\\Backups\\mandagdlog.trn'  
**WITH** FILE = 1, NOUNLOAD, STATS = 5, STOPAT = '2015-01-13T11:06:59'  
**ALTER** **DATABASE** \[Mandag\] **SET** MULTI\_USER  
**GO**

# Kryptering

#### create master key

use master  
**create** master **key** encryption **by** password ='Pa$$w0rd'  
\--Create server certificate  
**create** certificate Servercertificate  
**With** subject = 'Server level certificate'  
 

#### create database encryption key

use mandag  
**go**  
**create** **database** encryption **key**  
**with** algorithm = AES\_128  
encryption **by** server certificate ServerCertificate  
**go**  
 

#### Encrypt database

**alter** **database** mandag  
**set** encryption **on**  
**go**

#### backup / restore

backup **database** mandag **to** disk = 'R:\\Backups\\mandagfullkryptert.bak'  
  
\--  
\--source server  
\--  
use master  
**go**  
backup certificate ServerCertificate **to** file = 'r:\\Backups\\cert\\ServerCertificate.crt'  
**with** private **key** (file = 'r:\\Backups\\cert\\ServerCertificate.pvk',  
encryption **by** password = 'Pa$$w0rd' )  
**go**  
/\*  
  
\--  
\--destination server  
\--  
use master  
go  
create master key encryption by password = 'Pa$$w0rd'  
go  
create certificate ServerCertificate from file = 'r:\\Backups\\cert\\ServerCertificate.crt'  
with private key (file = 'r:\\Backups\\cert\\ServerCertificate.pvk',  
decryption by password = 'Pa$$w0rd' )  
go  
\*/

#### disable encryption

**alter** **database** mandag **set** encryption **off**  
use master  
**drop** **database** encryption **key**  
**drop** certificate ServerCertificate  
 

# Snapshot

#### Create snapshot

**create** **database** mandagSS **on**  
(name='mandag', filename='e:\\SS\\mandagss.mdf')  
**as** snapshot **of** Mandag  
 

#### Restore snapshot

restore **database** mandag **from**  
database\_snapshot = 'mandagSS'  
 

# Users

#### create SQL user

USE \[master\]  
**CREATE** LOGIN \[klaus\] **WITH** PASSWORD='Pa$$w0rd'  
 

#### create Windows user

USE \[master\]  
**CREATE** LOGIN \[ADVENTUREWORKS\\dbusers\] **FROM** WINDOWS

#### List users with info

**select** \* **from** sys.server\_principals

#### enable guest user

use mandag  
**grant** **connect** **to** guest

#### create database sql user

USE \[Mandag\]  
**CREATE** **USER** \[klaus\] **FOR** LOGIN \[klaus\]

#### create database AD user

USE \[Mandag\]  
**CREATE** **USER** \[ADVENTUREWORKS\\dbradley\] **FOR** LOGIN \[ADVENTUREWORKS\\dbradley\]

#### info om brukerere i database

use mandag  
**select** \* **from** sys.database\_principals

#### Create database role

USE \[Mandag\]  
**CREATE** **ROLE** \[DBBrukere\]

#### add user to database role

USE \[Mandag\]  
**ALTER** **ROLE** \[DBBrukere\] **ADD** MEMBER \[klaus\]

#### create schema in database

use mandag  
**go**  
**create** **schema** Personal  
**go**

#### change sid for sql user

use Mandag  
sp\_change\_users\_login 'update\_one', 'harald', 'harald'

#### list wrong sid for sql users

sp\_change\_users\_login 'report'

#### create sql user with specified sid

use master  
**create** login kari **with** password = 'Pa$$w0rd', SID=0xD2027DDCC55AC449BB43EC078D4D7B43

#### Transfer users from one server to another With passwords

[http://support2.microsoft.com/kb/918992](http://support2.microsoft.com/kb/918992)

# Maintenance plans

#### Index rebuild and integrity check

Should be run at least once a week, preferably every night
![Pasted image 20221206172859.png|undefined](/img/user/Windows/attachments/Pasted%20image%2020221206172859.png)
#### Full and log backup

Should run every day ( if not more often!)

Has email Notification for operators built in on failure

Also,cleans up old backup files

#### send mail from sql server (requiers public default profile)

msdb.dbo.sp\_send\_dbmail @recipients = 'administrator@adventureworks.com'  
, @subject = 'min første mail'  
, @body = 'Her var det mail'  
, @query = 'select \* from mandag.production.product'  
, @attach\_query\_result\_as\_file = 'true'  
, @query\_attachment\_filename = 'produktliste.csv'  
, @query\_result\_separator = ';'  
, @file\_attachments = 'E:\\newproducts.txt'  
, @exclude\_query\_output = 'true'  
, @query\_result\_header = 'false'  
, @query\_result\_no\_padding = 'true'

# LabFiler

[https://www.microsoft.com/learning/en-us/companion-moc.aspx](https://www.microsoft.com/learning/en-us/companion-moc.aspx)

#### Instruktør

Oscar Scharning

[os@glasspaper.no](mailto:os@glasspaper.no)
