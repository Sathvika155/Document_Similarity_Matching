# Document_Similarity_Matching
<h2>
  Overview
</h2>
<p>This task implements a document similarity matching system that takes an input invoice (PDF format) and compares it to a database of existing invoices. This program identifies the most similar invoice in the database based on content and structural similarity.This code extracts text from PDF invoices, converts the text into numerical vectors using TF-IDF, and measures the similarity using cosine similarity.</p>
<h2>
  Extracting Text From The InvoicePDF
</h2>
<p>
The provided code is a Python function that extracts text from a invoicePDF file using the PyMuPDF library, which is imported as "fitz". The function, "extract_text_from_pdf", takes a single argument "invoicepdf_path", which is the path to the PDF file. Inside the function, the PDF is opened using "fitz.open(invoicepdf_path)", resulting in a "form" object representing the PDF document. An empty string "text" is initialized to accumulate the extracted text. The function then iterates over each page of the PDF using a for loop. For each page, it loads the page with "form.load_page(pagenum)" and retrieves the text content of the page using "page.get_text()". The extracted text from each page is concatenated to the "text" string. After processing all pages, the function returns the combined text, providing a complete textual representation of the PDF's content. This function is useful for extracting and processing text from PDF documents for further analysis or comparison.    
</p>
<h2>
  Document Representation Method
</h2>
<p>
The provided code defines a Python function that converts a list of text documents into numerical vectors using the TF-IDF (Term Frequency-Inverse Document Frequency) method from the Scikit-learn library. The function, "Convert_textdocuments_into_numericalvectors", takes a single parameter "texts", which is a list of text documents. Within the function, an instance of "TfidfVectorizer" is created, named "tfidf_vectorizer". This vectorizer transforms the text documents into TF-IDF vectors, which numerically represent the importance of words in each document relative to the entire collection of documents. The method "fit_transform" of "tfidf_vectorizer" is called with the "texts" list as its argument. This method both fits the model to the data and transforms the text data into a sparse matrix of TF-IDF features, stored in "text_vectors". Finally, the function returns "text_vectors", which contains the numerical representation of the text documents, suitable for use in various machine learning and data analysis tasks. This conversion is essential for preparing textual data for algorithms that require numerical input.  
</p>
<h2>
  Similarity Metric
</h2>
<p>
  The provided code defines a function that identifies the most similar invoice to a new invoice from a list of existing invoices by comparing their textual content. The function, "find_most_similar_invoice", takes two parameters: "new_invoice_text", which is the text content of the new invoice, and "existing_invoices_texts", which is a list of text contents from the existing invoices. Inside the function, these texts are combined into a single list called "texts", with the new invoice text appended to the end. The function "vectorize_texts" (assumed to be defined elsewhere) is called to convert the list of text documents into numerical vectors using TF-IDF. The resulting vectors are stored in "vectors". Cosine similarity is used to measure the similarity between the TF-IDF vectors. Cosine similarity calculates the cosine of the angle between two vectors in a multidimensional space, providing a similarity score between 0 and 1, where 1 indicates identical vectors and 0 indicates orthogonal vectors.The cosine similarity between the vector of the new invoice (the last vector) and the vectors of the existing invoices is then calculated using "cosine_similarity". This function returns an array of similarity scores. The index of the highest similarity score is determined using "similarities.argmax()", which identifies the most similar invoice in the existing invoices. Finally, the function returns "most_similar_index", indicating the position of the most similar invoice in the list of existing invoices. This method effectively uses cosine similarity to measure the closeness of text documents in a high-dimensional space, making it useful for document matching tasks.
</p>
<h2>
  Paths To Train Invoices and Test Invoice
</h2>
<p>
  The provided code is responsible for finding the most similar invoice from a set of existing invoices based on the content of a new invoice. First, a list of paths to training invoices is defined in "train_invoice_paths", which contains the file paths to five existing PDF invoices stored on the user's desktop. A single path to a new invoice for testing is defined in "test_invoice_path". The code then extracts the text content from each existing invoice by using a list comprehension that calls the "extract_text_from_pdf" function for each path in "train_invoice_paths", storing the results in the "existing_invoices_texts" list. Similarly, the text of the new invoice is extracted and stored in the "new_invoice_text" variable. Subsequently, the function "find_most_similar_invoice" is called with the new invoice text and the list of existing invoice texts as arguments. This function computes the similarity between the new invoice and the existing invoices, returning the index of the most similar invoice. Finally, the program prints the path of the most similar invoice by accessing the "train_invoice_paths" list using the index obtained from the previous function, effectively informing the user which existing invoice closely matches the new invoice based on their textual content.
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
3.
<h2>Summary</h2>
->The program performs the following tasks:<br>
1.Extracts text content from a set of existing invoices and a new invoice.<br>
2.Converts the extracted text into numerical vectors using TF-IDF.<br>
3.Computes the cosine similarity between the new invoice and each existing invoice.<br>
4.Identifies and prints the path of the most similar existing invoice based on text content.<br>
<p>This approach uses text similarity to find the most similar invoice, making it effective for identifying invoices with similar wording and content. For more robust comparisons, especially considering layout and structure, additional features can be extracted and combined with text-based features.
</p>






