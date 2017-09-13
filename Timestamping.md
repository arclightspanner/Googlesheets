# Googlesheets
This function auto adds a date on a specific cell after a specific cell is filled out. In the code below, "Main" can be replaced with the 
name of the tab. 

    function onEdit() {
        var s = SpreadsheetApp.getActiveSheet(); 
        if( s.getName() == "Main" ) { //checks that we're on the correct sheet
        var r = s.getActiveCell();
        if( r.getColumn() == 1 ) { //checks the column
        var nextCell = r.offset(0, +2);
        if( nextCell.getValue() === '' ) //is empty?
        nextCell.setNumberFormat("MM/dd/YYYY")
        nextCell.setValue(new Date());
        }
       }
        if( s.getName() == "Main" ) { //checks that we're on the correct sheet
        var r = s.getActiveCell();
        if( r.getColumn() == 11 ) { //checks the column
        var nextCell = r.offset(0, +2);
        if( nextCell.getValue() === '' ) //is empty?
        nextCell.setNumberFormat("MM/dd/YYYY")
        nextCell.setValue(new Date());
        }
       }
      }
