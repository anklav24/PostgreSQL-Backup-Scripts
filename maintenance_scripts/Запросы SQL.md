### ������� ��������

`SELECT datid, datname, pid, usesysid, usename, application_name, client_addr, client_hostname, client_port, backend_start, query_start, state FROM pg_stat_activity;`

`PG_CANCEL_BACKEN`D ������������� ������������� �������� � ����
`SELECT pid, query, * FROM pg_stat_activity` -- ������� � ���������� ��. � ������ ������� postgres ������� PID ��������� PROCPID
`WHERE state <> 'idle' and pid <> pg_backend_pid();` -- ��������� ����������� � ���� ������ ��� ��������� �������

`SELECT pid, query, * FROM pg_stat_activity WHERE state <> 'idle' and pid <> pg_backend_pid();`

`SELECT pg_terminate_backend(PID);` /* ����������� ���� PID �������� ������� �� ����� ����������, � ������� �� ��������������� �������, �������� ����� ������� ������ � ����������, ������� �� ������ ����� ����� �������*/
`SELECT pg_cancel_backend(PID);` /* ����������� ���� PID �������� ������� �� ����� ����������. ����������� �������������� ������� ������, ���-�� ����� KILL -9 � LINUX */

### ���������� ������ ���

`\l`
`SELECT * FROM pg_database;`

### ���������� ������ ���

`\l+`

��� ������������ ������ (���������� ������� 4 ������)

`select t1.datname AS db_name,  
       pg_size_pretty(pg_database_size(t1.datname)) as db_size
from pg_database t1
order by pg_database_size(t1.datname) desc;`