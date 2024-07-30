# Document_Similarity_Matching
<h1>
  Overview
</h1>
<p>This task implements a document similarity matching system that takes an input invoice (PDF format) and compares it to a database of existing invoices. This program identifies the most similar invoice in the database based on content and structural similarity.This code extracts text from PDF invoices, converts the text into numerical vectors using TF-IDF, and measures the similarity using cosine similarity.</p>
<h1>
  Extracting Text From The InvoicePDF
</h1>
import fitz  # PyMuPDF
def extract_text_from_pdf(invoicepdf_path):
    form = fitz.open(invoicepdf_path)
    text = ""
    for pagenum in range(len(form)):
        page = form.load_page(pagenum)
        text += page.get_text() 
    return text
  <br>
<p>
The following code is a Python function that extracts text from a invoicePDF file using the PyMuPDF library, which is imported as "fitz". The function, "extract_text_from_pdf", takes a single argument "invoicepdf_path", which is the path to the PDF file. Inside the function, the PDF is opened using "fitz.open(invoicepdf_path)", resulting in a `form` object representing the PDF document. An empty string "text" is initialized to accumulate the extracted text. The function then iterates over each page of the PDF using a for loop. For each page, it loads the page with "form.load_page(pagenum)" and retrieves the text content of the page using "page.get_text()". The extracted text from each page is concatenated to the `text` string. After processing all pages, the function returns the combined text, providing a complete textual representation of the PDF's content. This function is useful for extracting and processing text from PDF documents for further analysis or comparison.    
</p>

