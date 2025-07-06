![PRECISE-Abreast Challenge Banner](https://github.com/PRECISE-Abreast-Challenge-PAC/PRECISE-Abreast-Challenge/blob/main/Resources/PRECISE-BANNER.jpg?raw=true)
# 🩺 Welcome to the PRECISE-Abreast Challenge
**PRECISE-Africa Breast Ultrasound Segmentation and Classification Challenge (PABC)**

Breast cancer is highly prevalent in Africa, with many women presenting at late stages due to limited awareness, diagnostic access, and cultural stigma. The lack of annotated breast imaging datasets representative of African populations also limits the effectiveness of AI in supporting early detection. Radiologist shortages, financial constraints, and societal barriers further complicate timely diagnosis and care, especially in rural and underserved areas.

The **PRECISE-Africa Breast Ultrasound Segmentation and Classification Challenge (PABC)** addresses these challenges by promoting **AI-driven solutions** using ultrasound data collected through the **ABreast Project**. This community-based initiative trains health workers to perform portable ultrasound exams and collect imaging data for machine learning. The challenge aims to develop accurate segmentation and classification algorithms tailored to African data, to improve with the aim of deploying these tools for early detection, enhancing diagnostic equity, and enabling scalable screening tools across low-resource settings

---

## 📝 Registration

To participate in the challenge, teams must complete the registration process by submitting their **team name** and member details through this **[Form](https://forms.office.com/r/40RFrz6XRJ)**.  
Each team can have up to **5 members**, including one designated **team leader**.  

Please make sure to provide accurate **Codabench usernames** for all team members, as this is required to grant access to the dataset and submission platform.

---

## 📝 Award Eligibility

To participate in the PRECISE-Abreast Challenge, applicants must:

- 🧑‍🎓 Be a **student, researcher, or clinician** in a relevant field, affiliated with an institution or organisation based in **Africa**  
- 🌍 Be **currently residing in Africa**  
- 🧾 Be **registered** for the **PRECISE Conference** and attend the **PRECISE-Abreast Workshop**, either **in person or online**  if participating as an individual or represented by a team member.
- 📄 Submit a **camera-ready paper** reporting the details of the methods in **Springer’s LNCS format**  
- ✅ Agree to the **Challenge Terms and Conditions**

---

## 🗃️ Dataset

The PRECISE-Abreast Challenge utilizes a curated, multi-institutional dataset of breast ultrasound (BUS) images to support the development and evaluation of algorithms for **lesion detection, classification, and segmentation**. The dataset integrates images from four distinct sources: 

- 📚 **BUSI** – Al-Dhabyani et al. (2020) [1]  
- 🧪 **BrEaST** – Pawłowska et al. (2024) [2]  
- 🔬 **BUS-BRA** – Gómez-Flores et al. (2024) [3]  
- 🌍 **ABreast** – an unpublished prospective collection of breast ultrasound scans from sub-Saharan Africa.

All images are paired with expert-verified reference annotations, including  **lesion boundaries** and **diagnostic labels** ( `normal`, `benign`, `malignant`.), enabling robust supervised learning and quantitative evaluation. The combined dataset reflects a wide range of ultrasound acquisition protocols and patient demographics to improve algorithmic fairness and clinical relevance.

**Phase I** includes **2,911  images across training and validation sets**, comprising
- 1,197 benign  
- 1,579 malignant  
- 134 normal  cases sourced from the **BUSI, BrEaST**, and **BUS-BRA** datasets.

**Phase II** introduces new annotated cases from the **ABreast dataset**. A **private test subset** will be reserved for the Test Phase and used for the final evaluation of submitted models, ensuring blind, unbiased assessment on African-representative data.

The dataset follows the naming convention outlined below:

**File naming convention**:
- `PABC`: Challenge name  
- `00001`: Subject ID  
- `000–101`: Scan type & diagnosis:
  - 000: Baseline – Normal  
  - 001: Baseline – Benign  
  - 002: Baseline – Malignant  
  - 100: Follow-up – Benign  
  - 101: Follow-up – Malignant  
- `DSET`: Dataset source tag, defined as:
  - `BUS`: `BUSI`, `BRE`: `BrEaST`, `BBR`: `BUS-BRA`, `ABR`: `Abreast`

**Example**: `PABC_00023_002_ABR` → Subject 00023, baseline malignant, sourced from ABreast dataset

Each ultrasound study includes a single **2D grayscale image** or a **Doppler image**, with resolutions varying based on the equipment used.

⚠️ Participants may **not** use any publicly available annotated datasets. However, they are permitted to use any published open-source models **ResNet-50** including **pretrained weights** from publicly available sources.


---

## 🧠 Task: Multi-Task Classification, Breast Lesion detection and Segmentation

🔍 Participants are required to design a single model that performs **multi-task learning**, simultaneously predicting the **breast-level diagnostic category** (`no lesion`, `benign lesion`, `malignant lesion`) and generating a **pixel-wise segmentation mask** of any visible lesion. This combined task reflects **real-world clinical workflows** where lesion detection, delineation, and diagnosis occur in parallel.

By emphasising both classification and segmentation in a single pipeline, the challenge encourages the development of robust, efficient, and clinically meaningful models suited for automated breast cancer assessment in resource-constrained settings.


🧪 The participants are called to upload their method in a **Cog container** for evaluation (more details under Evaluation)

---

## 📊 Evaluation Criteria

🏁 Performance will be assessed by averaging raw ranks across segmentation and classification metrics. Segmentation will be evaluated using **Lesion-wise Dice Similarity Coefficient (DSC)** and **Normalized Surface Dice (NSD)**, while classification will be measured by **Area Under the Curve (AUC)**, specificity at 90% sensitivity, and sensitivity at 90% specificity. All metrics will contribute equally to the final ranking.

### Segmentation:
- 🎯 Lesion-wise **Dice Similarity Coefficient (DSC)**
- 📐 **Normalized Surface Dice (NSD)**
-  📏 **95th Percentile Hausdorff Distance (HD95)**

### Classification:
- 📈 **AUC (Area Under the Curve)**
- ✅ **Specificity @ 90% sensitivity**
- ✅ **Sensitivity @ 90% specificity**

All evaluations will be performed on a **private test set** from the **ABreast dataset**.  
Details for the Cog containerized model test evaluation are provided on Github.


---

## 🏆 Awards

🎤 The **Top 3 contestants/teams** will be:
- Invited and mentored to present their work as part of  **MIRASOL-NextGen Interchange Workshop @ MICCAI 2026** (Abu Dhabi UAE)

🎓 **10 motivated participants** who demonstrated interest, motivation, leadership and determination will be shortlisted for **University of Pennsylvania Master of Science in Engineering in Data Science Scholarship.**

🏥 The **top 2 models** would be deployed for **clinical evaluation**

---

## 🗓️ Important Dates

📅 The challenge will run across multiple phases, including training, validation, and test periods.  
Please refer to the timeline below for key dates and deadlines:
![PRECISE-Abreast Timeline](https://github.com/PRECISE-Abreast-Challenge-PAC/PRECISE-Abreast-Challenge/blob/main/Resources/PRECISE-BANNER.jpg?raw=true)
---

## 👥 Abreast Data Contributors

- 🏥 **Ernest Cook Ultrasound Research and Education Institute** – Kampala, Uganda  
- 🏥 **Crestview Radiology Ltd** – Lagos, Nigeria

---

## 📬 Contact

Please contact us for further questions or comments via email:  **preciseabrestchallenge@gmail.com**

---

## 📚 References

-  [1] Al-Dhabyani, Walid, Mohammed Gomaa, Hussien Khaled, and Aly Fahmy. "Dataset of breast ultrasound images." Data in brief 28 (2020): 104863. 
-  [2]  Pawłowska, A., Ćwierz-Pieńkowska, A., Domalik, A., Jaguś, D., Kasprzak, P., Matkowski, R., Fura, Ł., Nowicki, A., & Zolek, N. A Curated benchmark dataset for ultrasound-based breast lesion analysis. Sci Data 11, 148 (2024). https://doi.org/10.1038/s41597-024-02984-z.  
-  [3] Gómez-Flores, Wilfrido, Maria Julia Gregorio-Calas, and Wagner Coelho de Albuquerque Pereira. "BUS-BRA: A breast ultrasound dataset for assessing computer-aided diagnosis systems." Medical Physics 51, no. 4 (2024): 3110-3123.