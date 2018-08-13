#Googlesheets
First step to sorting by color is to add a get hex function to gscript. 

     function getHexValue(range) {
     return SpreadsheetApp.getActiveSheet().getRange(range).getBackground();
     }

Moving forward you could obtain the hex value of the color in one specific cell by calling the function below

    =gethexvalue("N1")
