# Understanding the Best Index for Full-Document Queries in LlamaIndex

When working with **LlamaIndex**, selecting the right index depends on the type of query and the required depth of document understanding. Below are the best indexing strategies for questions that require a **comprehensive understanding of an entire document**.

![image](https://github.com/user-attachments/assets/d9cef73c-bada-4040-90c5-f49772a9103c)




## **Best Index Choices for Full-Document Understanding**

### **1. Summary Index** *(Best for High-Level Understanding & Global Context)*  
✅ **Use When:**
- You need to **generate a concise summary** of the document.
- The question requires a **broad understanding** rather than specific details.

🔹 **How It Works:**
- The document is summarized into a compact form.
- Queries retrieve responses based on this high-level summary.

🔹 **Example Use Case:**
```text
"What are the key takeaways from this ESG report?"
```

---

### **2. Tree Index (Hierarchical Indexing)** *(Best for Multi-Level Retrieval & Large Documents)*  
✅ **Use When:**
- The document is **very large**, and you want **structured retrieval**.
- Your question requires **understanding different sections** of a document.

🔹 **How It Works:**
- The document is indexed in a hierarchical structure (e.g., sections → subsections → paragraphs).
- Queries retrieve the most relevant **higher-level** summaries first, then drill down.

🔹 **Example Use Case:**
```text
"How does this company discuss carbon emissions in its ESG report?"
```
  - The index finds the relevant **chapter** first, then the **paragraph** discussing emissions.

---

### **3. Composability Index (Hybrid of Multiple Indexes)** *(Best for Mixed Granularity Retrieval)*  
✅ **Use When:**
- You need **both full-document understanding & detailed retrieval**.
- Your questions can vary between **broad summaries** and **specific details**.

🔹 **How It Works:**
- Combines multiple indexing strategies (e.g., Summary Index + Vector Index).
- Uses query routing to **decide which index** to use per query.

🔹 **Example Use Case:**
```text
"Summarize the ESG report and also find specific emission targets."
```
  - The query engine fetches **both the summary** and **retrieves emission targets**.

---

## **Choosing the Right Index**
| Index Type | Best For | Example Query |
|------------|---------|--------------|
| **Summary Index** | High-level overviews | "Give me a summary of this report" |
| **Tree Index** | Large documents with structured retrieval | "What does section X say about Y?" |
| **Composability Index** | Flexible, multi-purpose queries | "Summarize and extract emission data" |

## Detailed for choosing the right index

| Index Type            | How It Works | Best For | Querying Method | Use Case Example | Use Case Relevance (Your Notes) |
|-----------------------|-------------|----------|-----------------|------------------|-------------------------------|
| **Summary Index**     | Stores Nodes sequentially as a list. | Simple document summarization and linear retrieval. | Loads all Nodes or fetches top-k based on embedding/keywords. | Generating a summary of XYZ reports. | |
| **Vector Store Index** | Stores Nodes with corresponding embeddings in a vector store. | Semantic search and similarity-based retrieval. | Fetches top-k similar Nodes based on embeddings. | Retrieving relevant XYZ data from company reports based on similarity. | |
| **Tree Index**        | Builds a hierarchical tree structure from Nodes. | Structured, logical retrieval of hierarchical data. | Traverses from root to leaf nodes based on query. | Extracting structured insights from financial reports. | |
| **Keyword Table Index** | Extracts keywords from Nodes and maps them for retrieval. | Fast lookup of keyword-based queries. | Matches query keywords to pre-extracted keywords. | Quickly finding references to "Scope 1 Emissions" in XYZ documents. | |
| **Property Graph Index** | Creates a knowledge graph with labeled nodes and relationships. | Complex structured data, relationship-based queries. | Uses multiple retrievers (keyword, vector, synonym expansion, etc.). | Understanding relationships between sustainability metrics and company performance. | |


### **Which One Should You Use?**
- **For general document understanding → Summary Index**  
- **For structured retrieval in large documents → Tree Index**  
- **For flexible multi-purpose queries → Composability Index**  

---

## **Getting Started with LlamaIndex**
To implement one of these indexes, install LlamaIndex:
```bash
pip install llama-index
```
Then, choose your indexing strategy and apply it to your document processing pipeline.

---

### 🚀 Need Help?
If you have a specific use case, feel free to reach out and discuss the best indexing approach!
