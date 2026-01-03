# WifiPainPrediction

1. Exploratory Data Analysis (EDA)
→ Loaded the Internet Usage dataset and inspected its structure
→ Checked dataset shape, column names, datatypes, and missing values
→ Analyzed session start times, usage durations, uploads, downloads, and total data transferred
→ Identified peak usage hours and common session break reasons (e.g., Idle Timeout)
→ Observed that network load varies significantly by time of day

2. Preprocessing
→ Selected relevant columns related to network usage and timing
→ Converted start_time into datetime format
→ Extracted time-based features such as hour of day and late-night indicator (12–3 AM)
→ Converted usage_time into total usage duration in seconds
→ Converted upload and download values into numeric form and handled invalid entries
→ Removed or handled missing and infinite values

3. Feature Engineering
→ Created usage_seconds to represent session duration numerically
→ Computed data per second (session intensity) using total data transferred ÷ usage time
→ Engineered time-based features (hour, late-night flag) to capture peak congestion patterns
→ Combined duration, intensity, and time features to represent overall Wi-Fi load

4. Model Used
→ Built a Linear Regression model as a baseline
→ Built a Random Forest Regressor to capture non-linear relationships in network load
→ Split the dataset into training and testing sets (80/20)

5. Model Evaluation
→ Evaluated models using Mean Absolute Error (MAE) and R² score
→ Linear Regression achieved low R², showing limited ability to model complex patterns
→ Random Forest achieved strong performance (R² ≈ 0.91), indicating high predictive accuracy
→ Random Forest significantly outperformed the baseline model

6. Feature Importance Analysis
→ Analyzed feature importances from the Random Forest model
→ Found that usage duration (usage_seconds) and total data transferred contributed the most
→ Time-based features (hour, late-night) had smaller but meaningful influence
→ This confirmed that session intensity and duration drive Wi-Fi congestion more than time alone

7. Visualization & Insights
→ Visualized average network load by hour to identify peak congestion periods
→ Compared predicted vs actual Wi-Fi load values
→ Identified worst-case peak hours when Wi-Fi is slowest
→ Suggested optimal low-load hours for downloading or binge-watching

Files in this repository
wifi_load_prediction.ipynb — Full notebook with code and analysis
Internetusage.csv — Dataset
README.md — Explanation of the approach (this file)
