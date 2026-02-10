Cloud Anomaly Detection using Graph Features and ML

Project Overview
This project explores the detection of cloud attacks, such as Cryptojacking and Scanning, that try to stay hidden within normal organizational activity. My goal was to see if I could distinguish between legitimate users and attackers who operate within normal-looking statistical ranges.

My Methodology
Time Windows: I grouped the AWS CloudTrail logs into 1-hour windows to better understand user behavior over time.
Graph Features: I used the concept of Node Degree to see how many different services each user accessed, which helped in identifying scanning patterns.
Suspect Index: I created a simple formula to highlight when a user accesses services that are rarely used in the organization. It's calculated by dividing the Node Degree by the Service Popularity.

What I Learned (Results)
Initial Approach: My first attempt using an unsupervised model (Isolation Forest) resulted in an F1-score of 0.13 and many false alarms (44%). This showed me that looking for statistical outliers alone isn't enough.
Final Approach: By adding graph-based features and using AdaBoost, I was able to reach an F1-score of 1.00. This taught me how important it is to provide the model with the right context.

Findings
During the project, I was able to identify specific patterns:
- cloud_user: Showed a very high velocity of API calls, typical of Cryptojacking.
- sec_check and secmonkey: These accounts accessed more than 25 different services in a single hour, which signaled discovery activity.

How to Run
Note: Due to file size limits on GitHub, the data file (attack.json) is not included in this repository.

1. Open the .ipynb file in Google Colab.
2. Ensure you have the attack.json file available locally.
3. Upload the attack.json file to the Colab runtime environment (click the folder icon on the left sidebar and drag the file).
4. Run all cells to see the analysis and model results.

Conclusion
The main takeaway from this project for me was that while models are powerful, the way we prepare the data and incorporate domain knowledge (like graph theory) is what really makes the difference in identifying complex threats.
