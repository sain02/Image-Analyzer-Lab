# CST8917 – Lab 1: Azure Functions Text Analyzer
Course: CST8917 – Serverless Applications<br>
Student: Saizal Saini<br>
Student Number: 041168394
---

### Youtube Video Link 
https://youtu.be/veVhs8PCBqk

## 1. Objective

The objective of this lab was to build a serverless image processing system using Azure Durable Functions.  
The system automatically analyzes images uploaded to Blob Storage and stores the analysis results in Table Storage.  
The application was tested locally and then deployed to Microsoft Azure.

---

## 2. System Overview

The application follows an event-driven serverless architecture:

1. An image is uploaded to the **images** Blob container.
2. A Blob Trigger function detects the upload.
3. A Durable Function orchestrator is started.
4. Four activity functions run in parallel:
   - Analyze Colors
   - Analyze Objects
   - Analyze Text
   - Extract Metadata
5. The results are combined using the **Fan-Out / Fan-In pattern**.
6. The final analysis is stored in Table Storage.
7. An HTTP endpoint retrieves stored results.

---

## 3. Technologies Used

- Python 3.12
- Azure Functions
- Azure Durable Functions
- Azure Blob Storage
- Azure Table Storage
- Azurite (Local Emulator)
- Azure Storage Explorer
- Visual Studio Code

---

## 4. Local Development and Testing

- Used **Azurite** as the local storage emulator.
- Started the function using:

- Uploaded multiple image types (JPEG, PNG, grayscale).
- Verified orchestration and parallel execution in terminal logs.
- Retrieved results using:


The system successfully processed and stored multiple image analyses locally.

---

## 5. Deployment to Azure

- Created a Function App (Python 3.12, Linux, Consumption Plan).
- Created a Storage Account and `images` container.
- Added `ImageStorageConnection` in Application Settings.
- Deployed the project using the VS Code Azure Functions extension.
- Uploaded images to Azure Blob Storage.
- Retrieved results from the cloud endpoint:


Cloud execution worked successfully.

---

## 6. Security Considerations

- `local.settings.json` was not committed to GitHub.
- A `local.settings.example.json` file was created with placeholder values.
- Secrets and connection strings were stored securely in Azure Application Settings.

---

## 7. Conclusion

This lab demonstrated:

- Serverless architecture using Azure Functions
- Durable Functions orchestration
- Fan-Out / Fan-In parallel execution pattern
- Blob-triggered workflows
- Local testing and Azure cloud deployment

The project successfully analyzed images and stored results both locally and in Azure.

---
---

## THANKS