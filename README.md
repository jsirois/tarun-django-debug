Baseline stock from `django-admin startproject appsflyer` + Pants config:
```
$ git checkout baseline
$ ./pants run appsflyer/:manage -- createsuperuser

You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.
Traceback (most recent call last):
  File "/home/jsirois/.cache/pants/named_caches/pex_root/installed_wheels/031ccb717782f6af83a0063a1957686e87cb4581ea61b47b3e9addf60687989a/Django-4.1-py3-none-any.whl/django/db/backends/utils.py", line 89, in _execute
    return self.cursor.execute(sql, params)
  File "/home/jsirois/.cache/pants/named_caches/pex_root/installed_wheels/031ccb717782f6af83a0063a1957686e87cb4581ea61b47b3e9addf60687989a/Django-4.1-py3-none-any.whl/django/db/backends/sqlite3/base.py", line 357, in execute
    return Database.Cursor.execute(self, query, params)
sqlite3.OperationalError: no such table: auth_user
...
```

And switch to Postgres:
```
$ git checkout postgresql
$ ./pants run appsflyer/:manage -- createsuperuser
Traceback (most recent call last):
  File "/home/jsirois/.cache/pants/named_caches/pex_root/installed_wheels/031ccb717782f6af83a0063a1957686e87cb4581ea61b47b3e9addf60687989a/Django-4.1-py3-none-any.whl/django/db/backends/base/base.py", line 282, in ensure_connection
    self.connect()
  File "/home/jsirois/.cache/pants/named_caches/pex_root/installed_wheels/031ccb717782f6af83a0063a1957686e87cb4581ea61b47b3e9addf60687989a/Django-4.1-py3-none-any.whl/django/utils/asyncio.py", line 26, in inner
    return func(*args, **kwargs)
  File "/home/jsirois/.cache/pants/named_caches/pex_root/installed_wheels/031ccb717782f6af83a0063a1957686e87cb4581ea61b47b3e9addf60687989a/Django-4.1-py3-none-any.whl/django/db/backends/base/base.py", line 263, in connect
    self.connection = self.get_new_connection(conn_params)
  File "/home/jsirois/.cache/pants/named_caches/pex_root/installed_wheels/031ccb717782f6af83a0063a1957686e87cb4581ea61b47b3e9addf60687989a/Django-4.1-py3-none-any.whl/django/utils/asyncio.py", line 26, in inner
    return func(*args, **kwargs)
  File "/home/jsirois/.cache/pants/named_caches/pex_root/installed_wheels/031ccb717782f6af83a0063a1957686e87cb4581ea61b47b3e9addf60687989a/Django-4.1-py3-none-any.whl/django/db/backends/postgresql/base.py", line 215, in get_new_connection
    connection = Database.connect(**conn_params)
  File "/home/jsirois/.cache/pants/named_caches/pex_root/installed_wheels/57804fc02ca3ce0dbfbef35c4b3a4a774da66d66ea20f4bda601294ad2ea6092/psycopg2_binary-2.9.3-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl/psycopg2/__init__.py", line 122, in connect
    conn = _connect(dsn, connection_factory=connection_factory, **kwasync)
psycopg2.OperationalError: connection to server on socket "/var/run/postgresql/.s.PGSQL.5432" failed: No such file or directory
	Is the server running locally and accepting connections on that socket?
...
```
