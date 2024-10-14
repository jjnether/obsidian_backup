// This script should help BS writers and editors fix some common mistakes.

// Once you run the script, you should see changes in your document.

// If you run into any issues please contact maruta8268 or jjnether on discord

  

// !!!DO NOT TOUCH ANYTHING BELOW THIS POINT UNLESS YOU KNOW WHAT YOU ARE DOING!!!

  
  
  

function doGet(e) {

  return HtmlService.createHtmlOutputFromFile('index');

}

  

function editDocument(url) {

  if (!url) {

    return "Error: No URL provided.";

  }

  

  try {

    var doc = DocumentApp.openByUrl(url);

    var docName = doc.getName();  // Retrieve the document's name

    var body = doc.getBody();

    var sheetId = "1pB2FG2ICcpe57nHrzjnijXqpcquTG7a_iz73f6WWHWM"; // Google Sheet ID for capitalization fixes

  

    Logger.log("Document opened: " + docName + ". Starting replacements...");

  

    // Apply the replacements

    var ellipsesCount = replace_ellipses_characters(body);

    Logger.log("Ellipses replaced: " + ellipsesCount);

    var dashCount = replace_dash_characters(body);

    Logger.log("Dashes replaced: " + dashCount);

    var curlyQuotesCount = replace_curly_quotes(body);

    Logger.log("Curly quotes replaced: " + curlyQuotesCount);

    var trailingSpaceCount = remove_trailing_spaces(body);

    Logger.log("Trailing spaces removed: " + trailingSpaceCount);

  

    var capFixesCount = fix_capitalization_from_sheet(body, sheetId);

    Logger.log("Capitalization fixes made: " + capFixesCount);

  

    Logger.log("All replacements completed in " + docName);

    // Report the number of replacements back to the user

    var resultMessage = "Document '" + docName + "' has been processed:\n" +

                        "Replaced ellipses: " + ellipsesCount + "\n" +

                        "Replaced dashes: " + dashCount + "\n" +

                        "Replaced curly quotes: " + curlyQuotesCount + "\n" +

                        "Capitalization fixes made: " + capFixesCount + "\n" +

                        "Removed trailing spaces: " + trailingSpaceCount;

  

    return resultMessage;

  

  } catch (error) {

    Logger.log("Error opening or processing document: " + error.message);

    return "Error: " + error.message;

  }

}

  

// Optimized function for ellipses replacement

function replace_ellipses_characters(body) {

  var bodyText = body.getText();  // Get the body text as a string

  var ellipsesMatches = (bodyText.match(/…/g) || []).length;  // Count ellipses characters

  body.replaceText('…', '...');  // Replace ellipses

  return ellipsesMatches;  // Return the count of replacements

}

  

// Optimized function for dashes replacement

function replace_dash_characters(body) {

  var bodyText = body.getText();  // Get the body text as a string

  var emDashMatches = (bodyText.match(/—/g) || []).length;  // Count em dashes

  var enDashMatches = (bodyText.match(/–/g) || []).length;  // Count en dashes

  body.replaceText('—', '-');  // Replace em dashes

  body.replaceText('–', '-');  // Replace en dashes

  return emDashMatches + enDashMatches;  // Return the total count of dash replacements

}

  

// Optimized function for curly quotes replacement

function replace_curly_quotes(body) {

  var bodyText = body.getText();  // Get the body text as a string

  var openQuoteMatches = (bodyText.match(/“/g) || []).length;  // Count open curly quotes

  var closeQuoteMatches = (bodyText.match(/”/g) || []).length;  // Count close curly quotes

  body.replaceText('“', '"');  // Replace open curly quotes

  body.replaceText('”', '"');  // Replace close curly quotes

  return openQuoteMatches + closeQuoteMatches;  // Return the total count of curly quote replacements

}

  

// Optimized function for trailing spaces removal

function remove_trailing_spaces(body) {

  var bodyText = body.getText();  // Get the body text as a string

  var trailingSpacesMatches = (bodyText.match(/[ \t]+$/gm) || []).length;  // Count trailing spaces

  body.replaceText('([ \\t]+)$', '');  // Remove trailing spaces using regex

  return trailingSpacesMatches;  // Return the count of trailing spaces removed

}

  

// Uses a Google Sheet with pre-loaded words to fix capitalization mistakes

function fix_capitalization_from_sheet(body, sheetId) {

  // Open the Google Sheet by its ID

  var sheet = SpreadsheetApp.openById(sheetId).getActiveSheet();

  var data = sheet.getRange(2, 1, sheet.getLastRow() - 1, 2).getValues(); // Get data (skip header)

  

  var changesCount = 0;

  

  // Get the document's text

  var content = body.getText();

  

  // Loop through each row in the sheet and perform replacements

  data.forEach(function(row) {

    var wordToReplace = row[0];  // The word to replace (incorrectly capitalized)

    var replacementWord = row[1];  // The correct capitalization

  

    // Create a regex pattern that matches the word only when capitalization is incorrect

    var regex = new RegExp("\\b" + wordToReplace + "\\b", "g");

  

    // Find matches where the capitalization is incorrect (not equal to the correct word)

    var matches = content.match(regex);

  

    if (matches) {

      matches.forEach(function(match) {

        if (match !== replacementWord) {

          // Only replace the word if it doesn't match the correctly capitalized word

          content = content.replace(match, replacementWord);

          changesCount++;

        }

      });

    }

  });

  

  // Set the modified content back into the document

  body.setText(content);

  

  return changesCount; // Return the total number of replacements made

}