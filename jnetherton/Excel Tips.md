- After applying formulas, copy the formula cells and paste them back as values

**For text to the left of " := "**
=IFERROR(LEFT(A2,SEARCH(" := ",A2,1)-1),"")

**For text between " := " and "#" or to the right of " := " with no "#"**
=IFERROR(IFERROR(TRIM(MID(A2,SEARCH(" := ",A2)+4,SEARCH("#",A2,SEARCH(" := ",A2))-SEARCH(" := ",A2)-4)),TRIM(RIGHT(A2,LEN(A2)-SEARCH(" := ",A2)-3))),"")

**For text to the right of "#"**
=IFERROR(TRIM(RIGHT(A2,LEN(A2)-SEARCH("#",A2)-1)),"")


Sub Macro1()
'Best used when first column has value on last row and first row has a value in the last column

Dim sht As Worksheet
Dim LastRow As Long
Dim LastColumn As Long
Dim StartCell As Range
Dim objTable As ListObject

Set sht = Worksheets("Sheet1")
Set StartCell = Range("A1")

'Find Last Row and Column
  LastRow = sht.Cells(sht.Rows.Count, StartCell.Column).End(xlUp).Row
  LastColumn = sht.Cells(StartCell.Row, sht.Columns.Count).End(xlToLeft).Column

'Select Range
  sht.Range(StartCell, sht.Cells(LastRow, LastColumn)).Select
  Set objTable = ActiveSheet.ListObjects.Add(xlSrcRange, Selection, , xlYes)
End Sub