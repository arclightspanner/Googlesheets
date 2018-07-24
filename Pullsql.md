### This script is credited to my colleague Andy.

Upon opening, a new drop down menu will be created in googlesheets

    function onOpen() {
     var ui = SpreadsheetApp.getUi();
     ui.createMenu('Pulling_Function$')
     .addItem('Refresh data', 'readFromTable')
     .addSeparator()
     .addToUi();
    }

create a jdbc connection to the sql server

    var dbUrl = "jdbc:sqlserver://" + address + ";databaseName=" + db + ";user=" + user + ";password=" + userPwd + ";"

This is the function for the added item

    function readFromTable() {
      var start = new Date();
      var ss = SpreadsheetApp.getActiveSpreadsheet();
      var qtySheet = ss.getSheetByName('Sheet1'); //Put in title of Tab you'd like SQL to display in your sheet
      var conn = Jdbc.getConnection(dbUrl);
      var stmt = conn.createStatement();
      var results = stmt.executeQuery("SELECT * FROM XYZ"); //joins, temp tables and other SQL functions are runnable here
      var numCols = results.getMetaData().getColumnCount();
      var array = [['HEADER1','HEADER2','HEADER3']]; // this includes the header row
      while (results.next()) {
      var row = [];
      for (var col = 0; col < numCols; col++) {
      row.push(results.getString(col + 1));
      }
      array.push(row);
      }
      results.close();
      stmt.close();
      qtySheet.getRange('A:F').clear();
      qtySheet.getRange(1, 1, array.length, array[0].length).setValues(array);
      var end = new Date();
      var elapsed = (end-start)/1000; // in seconds
      ss.toast('Time elapsed: ' + elapsed + 'seconds');
      Logger.log('Time elapsed: %sms', end - start);
      }
