## ORM - SQLAlchemy
```Python
>>> import sqlalchemy
>>> sqlalchemy.__version__
'1.0.12'
>>> engine = sqlalchemy.create_engine('sqlite:///:memory:')
>>> engine.execute('SELECT 1').scalar()
1
>>> from sqlalchemy import Table, MetaData, Column, Integer, String
>>> metadata = MetaData()
>>> user =Table('users', metadata, 
...                 Column('id', Integer, primary_key=True), 
...                 Column('name', String(50)), 
...                 Column('fullname', String(50)), 
...                 Column('password', String(12))
... )
>>> class User(object):
...     def __init__(self, name, fullname, password):
...         self.name = name
...         self.fullname = fullname
...         self.password = password
... 
>>> from sqlalchemy.orm import mapper
>>> mapper(User, user)
<Mapper at 0x76ad080; User>
```
