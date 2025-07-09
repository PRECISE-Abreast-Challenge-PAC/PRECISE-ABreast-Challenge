## 📜 PRECISE-Abreast Challenge 2025 – Terms and Conditions

By registering for and participating in the **PRECISE-Abreast Challenge 2025** ("the Challenge"), you ("the Participant") agree to comply with the following Terms and Conditions. These terms are designed to ensure a fair, ethical, and impactful competition that aligns with the overarching mission of the PRECISE Symposium and its commitment to advancing equitable cancer diagnostics across Africa.

### 🔐 1. Eligibility
- Participation is open to **students, researchers, and clinicians** affiliated with an **institution based in Africa**.
- All participants must **currently reside in Africa** and be **registered for the PRECISE Conference 2025**.
- Participants may join individually or as part of a team, but at least one team member must attend the **PRECISE-Abreast Workshop** (virtually or in person).
- Participants must submit a **camera-ready paper** describing their methods in **Springer’s LNCS format** by the stated deadline.

### 📂 2. Data Use and Restrictions
- Participants are granted access to the training and validation datasets **solely for Challenge participation and research**.
- The use of any **external annotated breast ultrasound datasets is strictly prohibited**.  
  ✅ Open-source model architectures and pretrained weights (e.g., **ResNet-50**, **U-Net**) may be used.
- Redistribution or publication of the challenge data in any form without prior written permission is **not allowed**.
- Participants may **not attempt to de-anonymize** any patient information in the dataset.
- Teams may request to withdraw from the challenge at any time **before the start of the final testing phase**, provided they notify the organisers in writing.
- Withdrawals after results have been ranked or released will not be permitted.
- By submitting to the final test phase, participants acknowledge that their results may be included in rankings, publications, and summary analyses.


### 📦 3. Submission Requirements
- Each team must submit a single, **containerized (Cog-compatible)** model capable of performing **multi-task learning** (classification and segmentation) on the challenge data.
- All final submissions must adhere to the **technical instructions** provided in the official GitHub repository.
- Participants are required to submit an **accompanying method paper** detailing their approach.

### 📈 4. Evaluation and Ranking
Submissions will be evaluated using a combination of segmentation and classification metrics:

- **Classification:**  
  - AUC  
  - Specificity at 90% sensitivity  
  - Sensitivity at 90% specificity

- **Segmentation:**  
  - Lesion-wise Dice Similarity Coefficient (DSC)  
  - Normalized Surface Dice (NSD)  
  - 95th Percentile Hausdorff Distance (HD95)

🏁 Final rankings will be based on the **average of raw ranks across all metrics**.  
All evaluations will be conducted using a **private test set** derived from the **ABreast dataset**.

### 🏅 5. Awards and Recognition
- The **top three teams** will be invited to present their work at the **MIRASOL-NextGen Interchange workshop at MICCAI 2026**.
- Selected participants demonstrating strong potential and leadership will be **shortlisted for the University of Pennsylvania’s Master of Science in Engineering in Data Science Scholarship**.
- The **top two performing models** will undergo **clinical evaluation for deployment** in real-world screening settings.

### 💡 6. Intellectual Property and Open Science
- Participants retain **ownership of their submitted models and methods**.
- By participating, teams agree to allow the organizers to use submitted **results, method summaries**, and **anonymized visualizations** for **scientific dissemination, reporting**, and **educational purposes**.
- Participants are encouraged to share their **code and models publicly** under open-source licenses to promote transparency and reproducibility.

### 🙋🏿‍♂️ 7. Code of Conduct
- All participants must uphold a **professional and respectful standard of behavior** throughout the Challenge and associated events.
- Discrimination, harassment, or unethical behavior of any kind will result in **immediate disqualification**.
- The Challenge organizers reserve the right to **disqualify** any participant found violating these terms or engaging in **fraudulent activity**.

### ⚖️ 8. Amendments and Final Authority
- The organizers reserve the right to **modify rules, timelines, or evaluation criteria** in response to unforeseen circumstances.
- All decisions regarding **Challenge procedures, results, and awards** made by the organizing committee are **final and binding**.
