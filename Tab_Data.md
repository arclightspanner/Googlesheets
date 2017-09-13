#Googlesheets
The script below creates a sheet function that will return an array of all tabs included in the sheet.

    function sheetnames() {
       var out = new Array()
       var sheets = SpreadsheetApp.getActiveSpreadsheet().getSheets();
       for (var i=0 ; i<sheets.length ; i++) out.push( [ sheets[i].getName() ] )
       return out  
    }

With the information above, one could use the "indirect" function to pull any data referring to the tab name under the array.
    
    =INDIRECT("'"&A3&"'!"&"A3") //single cell
    =INDIRECT("'"&A3&"'!"&"A3:D6") //multiple cells
    
