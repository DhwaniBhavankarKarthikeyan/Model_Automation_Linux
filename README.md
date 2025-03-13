# **Automating Model Training & Deployment**  
### **1. Introduction**  
Machine learning models degrade over time as data patterns evolve. Manually training and deploying models is inefficient and error-prone. This script automates the training, evaluation, versioning, and deployment of an AI-powered fraud detection model.

---

## **2. Steps Involved in Automation**  

### **Step 1: User Input for Directory Locations**  
- The script prompts the user to enter paths for:  
  - **Data directory** (where new training data is stored)  
  - **Model storage directory** (where trained models are saved)  
  - **Deployment directory** (where the latest model is stored)  
  - **Log file path** (to store process logs)  

### **Step 2: Check for New Data**  
- The script verifies if new data is available in the specified directory.  
- If no new data is found, the script exits.  

### **Step 3: Train the Model**  
- Calls `train_model.py` with the new data.  
- Saves the trained model with a timestamped filename.  

### **Step 4: Evaluate the Model**  
- Calls `evaluate_model.py` to check the model’s performance.  
- Logs the evaluation results in the log file.  
- If the new model does not perform better than the previous version, deployment is skipped.  

### **Step 5: Deploy the Model**  
- If performance improves, the script:  
  - Copies the trained model to the deployment directory.  
  - Archives old models for version tracking.  

### **Step 6: Restart the Service**  
- Restarts the **fraud detection service** to apply the new model.  

---

## **3. Requirements**  
### **Software & Dependencies**  
- Linux/macOS environment  
- Python 3.x  
- Required Python libraries (`scikit-learn`, `pandas`, etc.)  
- Systemd (for restarting services)  

### **Python Scripts Used**  
1. `train_model.py` – Trains a fraud detection model.  
2. `evaluate_model.py` – Assesses model performance and logs results.  

---

## **4. How to Run the Script**  
1. **Ensure the required Python scripts (`train_model.py` and `evaluate_model.py`) are available.**  
2. **Make the shell script executable:**  
   ```bash
   chmod +x mlScript.sh
   ```  
3. **Run the script:**  
   ```bash
   ./mlScript.sh
   ```  

---

## **5. Version Control & Tracking**  
- Trained models are saved with timestamps.  
- Old models are archived for future reference.  
- Log files track each training and deployment event.  

