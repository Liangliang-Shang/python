## ORM - SQLAlchemy
```Python
>>> import sqlalchemy
>>> sqlalchemy.__version__
'1.0.12'
>>> engine = sqlalchemy.create_engine('sqlite:///:memory:', echo=True)
>>> engine.execute('SELECT 1').scalar()
2016-11-03 17:52:23,069 INFO sqlalchemy.engine.base.Engine SELECT CAST('test plain returns' AS VARCHAR(60)) AS anon_1
2016-11-03 17:52:23,069 INFO sqlalchemy.engine.base.Engine ()
2016-11-03 17:52:23,071 INFO sqlalchemy.engine.base.Engine SELECT CAST('test unicode returns' AS VARCHAR(60)) AS anon_1
2016-11-03 17:52:23,071 INFO sqlalchemy.engine.base.Engine ()
2016-11-03 17:52:23,072 INFO sqlalchemy.engine.base.Engine SELECT 1
2016-11-03 17:52:23,072 INFO sqlalchemy.engine.base.Engine ()
1
>>> 
```
