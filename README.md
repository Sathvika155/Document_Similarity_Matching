# Document_Similarity_Matching
<h2>
  Overview
</h2>
<p>This task implements a document similarity matching system that takes an input invoice (PDF format) and compares it to a database of existing invoices. This program identifies the most similar invoice in the database based on content and structural similarity.This code extracts text from PDF invoices, converts the text into numerical vectors using TF-IDF, and measures the similarity using cosine similarity.</p>
<h2>
  Extracting Text From The InvoicePDF
</h2>
<p>
The provided code defines a Python function, "extracting_text_from_invoicepdf", which extracts text from a PDF invoice file using the PyMuPDF library, imported as "fitz". The function takes a single argument, "invoicepdf_path", representing the path to the PDF. It opens the PDF and initializes an empty string to accumulate the extracted text. The function iterates through each page, loading it and retrieving the text content using "page.get_text()", appending the extracted text to the string. After processing all pages, the function returns the combined text, making it useful for further analysis or comparison of PDF documents.  
</p>
<h2>
  Document Representation Method
</h2>
<p>
The code defines a function, "Convert_textdocuments_into_numericalvectors", which converts a list of text documents into numerical vectors using the TF-IDF (Term Frequency-Inverse Document Frequency) method from the Scikit-learn library. It takes a list of text documents as input and creates an instance of "fidfVectorizer". The "fit_transform" method is called to fit the model to the data and transform the text into a sparse matrix of TF-IDF features, which represents the importance of words in each document relative to the entire collection. The function then returns this matrix, enabling the use of textual data in machine learning and data analysis tasks that require numerical input. 
</p>
<h2>
  Similarity Metric
</h2>
<p>
  The code defines a function, "finding_most_similar_invoice", which identifies the most similar invoice to a new one from a list of existing invoices based on their textual content. It takes the text of the new invoice and a list of texts from existing invoices, combines them, and converts them into numerical vectors using TF-IDF. Cosine similarity is then calculated between the new invoice vector and each existing invoice vector, providing a similarity score between 0 and 1. The index of the highest similarity score, found using "similarities.argmax()", indicates the most similar invoice. This method effectively uses cosine similarity to measure document similarity, making it suitable for matching invoices.
</p>
<h2>
  Paths To Train Invoices and Test Invoice
</h2>
<p>
 The code identifies the most similar invoice from a set of existing ones based on the content of a new invoice. It defines file paths to five existing invoices and one new invoice, extracts the text from these invoices, and stores them in lists. Using the "finding_most_similar_invoice" function, it computes the similarity between the new invoice and the existing ones, returning the index of the most similar invoice. The path of the most similar invoice is then printed, indicating which existing invoice closely matches the new one based on textual content.
</p>
<h2>
  Instructions To Run The Code
</h2>
<h3>Prerequisites</h3>
->Python 3.x<br>
->Required Python packages:<br>
1.PyMuPDF<br>
2.scikit-learn<br>
You can install the required packages using the following command:<br>
pip install pymupdf scikit-learn<br>
<h3>Running the Code</h3>
->Clone the repository or download the text.ipynb to your app like (VSCode,Jupyter,Google Collab).<br>
->Prepare your PDF files:<br>
1.Place the train invoices in a folder.<br>
2.Ensure the new invoice to be compared is available.<br>
->Update the paths in the script:<br>
1.Modify the train_invoice_path list with the paths to your existing invoice PDFs.<br>
2.Modify the test_invoice_path with the path to your new invoice PDF.<br>
<h2>Summary</h2>
->The program performs the following tasks:<br>
1.Extracts text content from a set of existing invoices and a new invoice.<br>
2.Converts the extracted text into numerical vectors using TF-IDF.<br>
3.Computes the cosine similarity between the new invoice and each existing invoice.<br>
4.Identifies and prints the path of the most similar existing invoice based on text content.<br>
<p>This approach uses text similarity to find the most similar invoice, making it effective for identifying invoices with similar wording and content. For more robust comparisons, especially considering layout and structure, additional features can be extracted and combined with text-based features.
</p>






