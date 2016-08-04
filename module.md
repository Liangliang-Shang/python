## xlwt
```Python
import xlwt
workbook	= xlwt.Workbook()
sheeta		= workbook.add_sheet('sheeta', cell_overwrite_ok=True)
sheetb		= workbook.add_sheet('sheetb', cell_overwrite_ok=True)
style 		= xlwt.XFStyle()
font		= xlwt.Font()
font.name	= 'Times New Roman'

for row in range(4):
	for col in range(4):
		for sheet in (sheeta, sheetb):
			if row == col:
				font.bold	= True
				font.italic	= True
				style.font	= font
			else:
				font.bold	= False
				font.italic	= False
				style.font	= font
			sheet.write(row, col, 
				''.join(['Row', str(row), 'Col', str(col)]), style)
workbook.save('xlwt.xls')
```
## Pickle
```python
import pickle
fName		= ""
fSuffix		= 'pickle'
fPickle		= '.'.join([fName, fSuffix])
i			= 19700101
s			= 'Python'
l			= range(10)
d			= { '97': 'a', '98': 'b' }
with open(fPickle, 'wb') as f: 
	pickle.dump((i, s, l, d), f)

with open(fPickle, 'rb') as f: 
	i, s, l, d = pickle.load(f)
	print i, s, l, d
```

    19700101 Python [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] {'98': 'b', '97': 'a'}
    
## numpy, pandas, matplotlib.pyplot, matplotlib.dates
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.dates as mdate
idx  = pd.date_range(start='09:15:00', end='14:55:00', freq='5min')
nidx = pd.date_range(start='09:30:00', end='14:30:00', freq='30min')
df   = pd.DataFrame(np.random.randn(len(idx)), index=idx, columns=list('A'))
fig, ax = plt.subplots()
ax.plot(df)
ax.xaxis.set_major_formatter(mdate.DateFormatter('%H:%M'))
plt.xticks(nidx.insert(0, idx[0]).insert(-1, idx[-1]))
for xl in ax.get_xticklabels():
    xl.set_rotation(45)
plt.grid(True)
plt.show()
```
