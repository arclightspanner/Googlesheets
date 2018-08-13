The first step to sorting bg color is to add a get hex function to tools -->> script editor. 

     function getHexValue(range) {
     return SpreadsheetApp.getActiveSheet().getRange(range).getBackground();
     }

Now you can obtain the hex value of the color in one specific cell by calling the function below

    =gethexvalue("N1")

To be able to sort your column by color, you'll need to get the hex value of all column cells, since gethexvalue requires string as input, this might be a problem. To work around this, you'll need to create a placeholder column that holds the cell name. 

For instance, in column A1 type in string A1, for A2 type in A2 etc., click on the little dot next to your cell to automate this process if your cell is next to a column that contains text. Then use =gethexvalue(A1) and it'll be usable on cells.

Once you are able to generate all hex values for each row, you can sort those hex values by row. 
