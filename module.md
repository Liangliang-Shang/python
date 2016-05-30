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
