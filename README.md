# project_united_airlines
# United Airlines Call Center Optimization Project

## Problem Statement
United Airlines strives to provide world-class customer service and enhance operational efficiency through its call center operations. Two critical performance metrics—**Average Handle Time (AHT)** and **Average Speed to Answer (AST)**—are areas where improvements are sought. This project aims to optimize these key call center metrics by analyzing existing data to identify inefficiencies, determine the drivers of long AHT and AST, and propose strategies to reduce resolution times, improve customer satisfaction, and streamline operations.

### Key Focus Areas
1. **Average Handle Time (AHT):**  
   The total time agents spend on a call from answering to disconnecting. Reducing this metric increases the number of calls agents can handle without compromising the quality of service.

   - **Formula:**  
     ```AHT = Total Handle Time / Total Number of Calls```

2. **Average Speed to Answer (AST):**  
   The total time customers spend in queue before being assisted by an agent. Minimizing AST improves customer satisfaction by reducing wait times.

   - **Formula:**  
     ```AST = Total Waiting Time / Total Number of Calls```

## Objective
- Analyze call center data to identify factors contributing to high AHT and AST.
- Suggest improvements to the call center's operations, especially in:
  - Reducing call escalations that could be handled through self-service options.
  - Enhancing customer experience and operational efficiency through optimized IVR (Interactive Voice Response) systems.
  
## Deliverables
1. **Data Analysis:**  
   Perform in-depth analysis of the call center data to:
   - Identify drivers for long AHT and AST, especially during peak call periods.
   - Quantify the percentage difference between AHT for the most frequent and least frequent call reasons.
   
2. **Self-Service Optimization:**  
   Analyze call transcripts and reasons to identify recurring issues that could be addressed via IVR, reducing the need for agent intervention.

3. **Call Categorization:**  
   Analyze and categorize call reasons to improve routing and reduce manual tagging efforts. Suggest feature identification techniques for future improvements.

4. **Code & Predictions:**  
   Provide Python/SQL/R scripts to run the analysis, along with instructions for use. An optional submission of predictions (`test.csv`) is welcome.
   - Columns for `test.csv`:
     - `call_id`: Unique identifier for each call.
     - `primary_call_reason`: Predicted primary reason for the call.

## Approach
### Data Cleaning and Preprocessing
1. **Missing Values:** Handle missing values, especially in `mp_status`, `agent_tone`, and `customer_tone`.
2. **Feature Engineering:** Create new features such as `call_duration`, `wait_time`, and sentiment-based features from the call transcript.

### Exploratory Data Analysis (EDA)
1. **AHT Analysis:**  
   - Analyze call types, agent performance, and customer sentiment to understand the drivers of long handle times.
   
2. **AST Analysis:**  
   - Investigate call volume and customer behavior during peak times.
   
3. **Sentiment Analysis:**  
   - Use NLP techniques on call transcripts to analyze customer and agent sentiment, correlating it with call outcomes and escalations.

### Machine Learning Model
1. **Feature Selection:**  
   - Identify important features such as `customer_tone`, `agent_tone`, and `average_sentiment`.
   
2. **Model Training:**  
   - Train a classification model to predict the `primary_call_reason` based on the provided dataset.

### SQL Query for AHT Calculation:
``sql
SELECT
    AVG(call_end_datetime - agent_assigned_datetime) AS avg_handle_time
FROM
    call_center_data;


## Data Dictionary

| Column Name              | Description                                          |
|--------------------------|------------------------------------------------------|
| `call_id`                 | Unique identifier for each call                      |
| `customer_id`             | Unique identifier for the customer                   |
| `agent_id`                | Unique identifier for the agent handling the call    |
| `call_start_datetime`     | Date and time when the call started                  |
| `agent_assigned_datetime` | Date and time when the agent answered the call       |
| `call_end_datetime`       | Date and time when the call ended                    |
| `customer_name`           | Name of the customer                                 |
| `mp_status`               | Customer loyalty status (NaN, 0, 1, 2, 3, 4, 5)     |
| `agent_tone`              | Detected tone of the agent during the call           |
| `customer_tone`           | Detected tone of the customer during the call        |
| `average_sentiment`       | Sentiment score of the entire conversation           |
| `silence_percent_average` | Average percentage of silence in the call            |
| `call_transcript`         | Full transcript of the conversation between agent and customer |
| `primary_call_reason`     | Detected primary reason for the customer's call      |


