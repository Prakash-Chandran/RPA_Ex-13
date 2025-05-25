# RPA_Ex-13

# Ex-13-Invoice-Processing-automation-using-OCR

~~~
Name : PRAKASH.C
Reg.No : 212223240122
~~~

## Aim
To automate the extraction of key information (Invoice Number, Date, and Total Amount) from a scanned invoice PDF using OCR technology in UiPath and store the extracted data into an Excel file.

## Materials Required
UiPath Studio

Tesseract OCR or Microsoft OCR (included in UiPath)

Invoice PDF file (scanned or image-based)

UiPath.Excel.Activities

UiPath.PDF.Activities

Basic understanding of Regular Expressions (Regex)

Microsoft Excel

## Procedure
### Step 1: Prepare the Project
Create a new project in UiPath Studio called InvoiceOCRBot.

Place your Invoice PDF in the project folder for easy access.

### Step 2: Read the Invoice using OCR
Use the Read PDF with OCR activity (from UiPath.PDF.Activities).

Set the file path to your invoice PDF.

Use Tesseract OCR or Microsoft OCR engine.

Output: ocrText (String variable)

### Step 3: Extract Data Using Regex
Use Assign activities to extract data:

~~~
invoiceNumber = System.Text.RegularExpressions.Regex.Match(ocrText, "Invoice Number[:\s]*([A-Za-z0-9\-]+)").Groups(1).Value  
invoiceDate = System.Text.RegularExpressions.Regex.Match(ocrText, "Date[:\s]*([0-9\/\-]+)").Groups(1).Value  
totalAmount = System.Text.RegularExpressions.Regex.Match(ocrText, "Total Amount[:\s]*([\d,]+\.\d{2})").Groups(1).Value
~~~

 ### Step 4: Create and Write to Excel
Use a Build Data Table activity to create a table with columns:
Invoice Number, Date, Total Amount

Use Add Data Row to insert extracted values.

Use Write Range activity to save the data to InvoiceData.xlsx.

### Step 5: Run and Verify
Run the bot.

Open the InvoiceData.xlsx file to check if the data is entered correctly.

## OUTPUT:

![13-1](https://github.com/user-attachments/assets/e4d9abeb-8e49-4130-936d-9855c6683b82)

![13-2](https://github.com/user-attachments/assets/d3908fc9-b765-4c20-af7c-5a0b0ca6949e)

![13-3](https://github.com/user-attachments/assets/58afe8ca-f3f2-465c-9a05-5f7be16ce975)

## Result
The UiPath robot successfully extracted key data from an image-based PDF using OCR and saved it in an Excel file for further use.
