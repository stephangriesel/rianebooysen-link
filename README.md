# rianebooysen.com

### How to edit script:

1. Go to sheet file
2. Extensions
3. App Script

### How to remove icons:

1. Go to sheet file
2. Clear cell

### Example sheet:

```
The status enabled can be cleared and only applies if header hero needs to be displayed
```

```
Facebook,fab fa-facebook fa-2x,https://www.yourlink.com, enabled
Instagram,fab fa-instagram fa-2x,https://www.yourlink.com, enabled
X,fa-brands fa-x-twitter fa-2x,https://www.yourlink.com, enabled
LinkedIn,fab fa-linkedin fa-2x,https://www.yourlink.com, enabled
GitHub,fab fa-github fa-2x,https://www.yourlink.com, enabled
```

<details>
  <summary>Technical Details</summary>
```
function doGet() {
  // Get a reference to the active spreadsheet
  const doc = SpreadsheetApp.getActiveSpreadsheet();
  console.log("Active Spreadsheet:", doc.getName()); // Log the active spreadsheet name

// Get a reference to the sheet named "Social"
const sheet = doc.getSheetByName("Social");
console.log("Sheet object:", sheet); // Log the sheet object itself

// Retrieve values from a range of cells:
// - Starts at cell A1 (column 1, row 1)
// - Includes 10 rows
// - Includes 6 columns
const values = sheet.getRange(1, 1, 10, 6).getDisplayValues();
console.log("Retrieved values:", values); // Log the retrieved 2D array of values

// Transform the 2D array of values into an array of objects:
const result = values.map((s) => ({
name: s[0],
icon: s[1],
link: s[2],
status: s[3],
description: s[4],
iconDescription: s[5],
}));
console.log("Transformed result:", result); // Log the final array of objects

// Create a JSON response containing the transformed data:
return ContentService.createTextOutput(JSON.stringify({data: result})).setMimeType(ContentService.MimeType.JSON);
}

```

```

More details here: https://developers.google.com/apps-script/guides/web

</details>

<details>
  <summary>Change Log</summary>
  04/04/2024 - Clear data
  03/04/2024 - Dynamically render page title
  10/04/2024 - Update border
</details>
```
