# NLP-Automated-Text-Extraction-Model

## **Overview**  
This project is an **AI-powered resume parsing system** that uses **spaCy for Named Entity Recognition (NER)** and **MongoDB for database pipelining**. The model extracts and analyzes key resume details such as **name, contact information, skills, education, work experience, and certifications**.  

## **Key Features**  
✅ **Extracts text from DOCX and PDF resumes**  
✅ **Preprocesses text by removing noise and structuring data**  
✅ **Trains a spaCy NER model with labeled resume data**  
✅ **Uses MongoDB for seamless data storage and retrieval**  
✅ **Deploys a pipeline for real-time resume parsing and analysis**  

---

## **Tech Stack**  
- **Python** – Core programming language  
- **spaCy** – NER-based text processing  
- **pdfplumber** – PDF text extraction  
- **zipfile & xml.etree.ElementTree** – DOCX parsing  
- **MongoDB** – Database for storing structured resume data  
- **Flask** – (Optional) API deployment  

---

## **Installation & Setup**  

### **1. Clone the Repository**  
```sh
git clone https://github.com/your-repo/nlp-resume-parser.git
cd nlp-resume-parser
```

### **2. Install Dependencies**  
```sh
pip install -r requirements.txt
```
Ensure `requirements.txt` includes:
```
spacy
pdfplumber
pymongo
Flask  # Optional for API
```

### **3. Download spaCy Model**  
```sh
python -m spacy download en_core_web_lg
```

### **4. Set Up MongoDB (Optional)**  
- Create a **MongoDB database** (`resume_db`)  
- Create a collection for **NER training data** (`ner_training_data`)  
- Update `MONGO_URI` in the script with your MongoDB connection string  

---

## **Usage**  

### **1. Extract Resume Text**  
Modify the `folder_path` in the script to point to your resume folder, then run:  
```sh
python extract_resumes.py
```
This extracts and cleans text from all DOCX and PDF files.

### **2. Train the NER Model**  
To train the **custom spaCy NER model**, run:  
```sh
python train_ner.py
```
This script:  
✅ Loads **training data from MongoDB**  
✅ **Fine-tunes the NER model** with domain-specific labels  
✅ Saves the trained model for **real-time resume parsing**  

### **3. Parse Resumes in Real-Time**  
Once trained, the model can be used to analyze resumes:  
```sh
python parse_resume.py --resume "sample_resume.pdf"
```
The output will be structured data containing extracted details like **name, email, phone, skills, education, etc.**.

---

## **How It Works**  

### **🔹 Step 1: Data Extraction**  
- Extracts text from **PDF and DOCX** resumes using **pdfplumber** and **XML parsing**.  
- Cleans and structures the extracted text.  

### **🔹 Step 2: Named Entity Recognition (NER) Training**  
- Uses **spaCy’s NER** model with custom labels:  
  `["NAME", "EMAIL", "PHONE", "DEGREE", "UNIVERSITY", "COMPANY", "JOB_TITLE", "SKILL", "CERTIFICATION"]`  
- **Training data is stored in MongoDB**, allowing easy retrieval and updates.  
- The model **fine-tunes NER using annotated resumes**.  

### **🔹 Step 3: Database Pipelining with MongoDB**  
- Extracted resume data is **stored in MongoDB** for further processing.  
- Allows **continuous learning** by updating training data dynamically.  

### **🔹 Step 4: Real-Time Resume Parsing**  
- The trained model processes **new resumes in real-time**, extracting key details for further analysis or integration with **ATS (Applicant Tracking Systems)**.  

---

## **Example Output**  
After processing a resume, the model returns structured data like this:  
```json
{
    "Name": "John Doe",
    "Email": "johndoe@example.com",
    "Phone": "+1 123-456-7890",
    "Education": [
        {
            "Degree": "B.Tech",
            "University": "MIT",
            "Year": "2022"
        }
    ],
    "Experience": [
        {
            "Job Title": "Software Engineer",
            "Company": "Google",
            "Years": "2"
        }
    ],
    "Skills": ["Python", "Machine Learning", "NLP", "SQL"]
}
```

---

## **Future Enhancements**  
🔹 **Improve accuracy** using transformer-based models like `BERT` or `GPT-4`  
🔹 **Deploy as an API** using `FastAPI` or `Flask`  
🔹 **Enhance model performance** with **larger training datasets**  

---

## **Contributors**  
👤 **Gayatri Ghorpade** – Lead Developer  
📧 **Contact:** gayatrighorpade409@gmail.com 

---
