![PRECISE-Abreast Challenge Banner](https://github.com/PRECISE-Abreast-Challenge-PAC/PRECISE-Abreast-Challenge/blob/main/Resources/images/PRECISE.jpg?raw=true)
# 🩺 Welcome to the PRECISE-ABreast Challenge
**PRECISE-Africa Breast Ultrasound Segmentation and Classification Challenge (PACE)**

Breast cancer is highly prevalent in Africa, with many women presenting at late stages due to limited awareness, diagnostic access, and cultural stigma. The lack of annotated breast imaging datasets representative of African populations also limits the effectiveness of AI in supporting early detection. Radiologist shortages, financial constraints, and societal barriers further complicate timely diagnosis and care, especially in rural and underserved areas.

The **PRECISE-Africa Breast (ABreast) Ultrasound Segmentation and Classification Challenge (PACE)** addresses these challenges by promoting **AI-driven solutions** using ultrasound data collected on African women through the **ABreast Project**. This community-based initiative improves access to breast cancer screening in vulnerable underserved communities using portable ultrasound scans performed in the community and enhanced tumor imaging using machine learning. The PACE Challenge aims to develop accurate segmentation and classification algorithms tailored to African breast ultrasound data, to advance the deployment of these accessible point-of-care tools for early detection, enhancing diagnostic equity, and enabling scalable screening tools across low-resource settings.

---

## 📝 Registration

To participate in the challenge, teams must complete the registration process by submitting their **team name** and member details through this **[Form](https://forms.office.com/r/40RFrz6XRJ)**.  
Each team can have up to **5 members**, including one designated **team leader**.  

Please make sure to provide accurate **Codabench usernames** for all team members, as this is required to grant access to the dataset and submission platform.

📜 **Registration Guidelines:**  
Please refer to the [Registration README](https://github.com/PRECISE-Abreast-Challenge-PAC/PRECISE-Abreast-Challenge/blob/main/registration.md) for complete instructions.

---

## 📝 Award Eligibility

To participate in the PRECISE-ABreast Challenge, participating teams must meet the following requirements:

- 🧑‍🎓 Have active members who are students, researchers, or clinicians in a relevant field, affiliated with an institution or organisation based in **Africa**  
- 🌍 Must have at least one or two active members who **currently residing in Africa**  
- 🧾 Have active members who are registered to attend the **PRECISE Conference** and committed to attending the **PRECISE-ABreast Workshop,** either in person or Online, if participating as an individual or represented by a team member..
- 📄 Submit a **camera-ready paper** reporting the details of the methods in **[Springer’s LNCS conference proceedings format](https://www.springer.com/gp/computer-science/lncs/conference-proceedings-guidelines?srsltid=AfmBOoqal5rcgwA-guJYqKR6WYb1NlPmMBZsFUNnys7gqkakP6V2XJZL)**  
- ✅ Must agree to the **PRECISE-ABreast Challenge Terms and Conditions**

---

## 🗃️ Dataset

The PRECISE-ABreast Challenge utilizes a curated, multi-institutional dataset of breast ultrasound (BUS) images to support the development and evaluation of algorithms for lesion detection, classification, and segmentation. The dataset integrates images from four distinct sources: the BUSI dataset by Al-Dhabyani et al. (2020)[1], the BrEaST dataset by Pawłowska et al. (2024)[2], the BUS-BRA dataset by Gómez-Flores et al. (2024)[3], and the ABreast point-of-care dataset, an unpublished prospective collection of breast handheld ultrasound scans from community-dwelling women in sub-Saharan Africa.

All images are paired with expert-verified reference annotations, including **lesion boundaries** and diagnostic labels (`normal, benign, malignant`), enabling robust supervised learning and quantitative evaluation. The combined dataset reflects a wide range of ultrasound acquisition protocols and patient demographics to improve algorithmic fairness and clinical relevance.

**Phase I** of the challenge includes **7,354  images across training and validation sets**, comprising
- 4,574 benign  
- 2,248 malignant  
- 532 normal  cases sourced from the **BUSI, BrEaST**, and **BUS-BRA** datasets.

**Phase II** will introduce additional annotated cases from the **ABreast dataset**. A private subset of ABreast data will be reserved for the Test Phase and used for the final evaluation of submitted models, ensuring a blind, unbiased assessment of African-representative data.

The dataset follows the naming convention outlined below:

**File naming convention**:
- `PACE`: Name of the challenge  
- `00001`: Subject ID  
- `000–101`: Scan timepoint and diagnostic status, defined as:
  - 000: Baseline – Normal  
  - 001: Baseline – Benign  
  - 002: Baseline – Malignant  
  - 100: Follow-up – Benign  
  - 101: Follow-up – Malignant  
- `DSET`: Dataset source tag, defined as:
  - `BUS`: `BUSI`, `BRE`: `BrEaST`, `BBR`: `BUS-BRA`, `ABR`: `Abreast`

**Example**: `PACE_00023_002_ABR` → Subject 00023, baseline malignant, sourced from ABreast dataset

Each ultrasound study includes a single **2D grayscale image** or a **Doppler image**, with resolutions varying based on the equipment used.

⚠️ Participants may **not** use any publicly available annotated datasets. However, they are permitted to use any published open-source models **ResNet-50** including **pretrained weights** from publicly available sources.


---

## 🧠 Task: Multi-Task Classification, Breast Lesion detection and Segmentation

🔍 Participants are required to design a single model that performs **multi-task learning**, simultaneously predicting the **breast-level diagnostic category** (no lesion, benign lesion, malignant lesion) and generating a **pixel-wise segmentation mask** of any visible lesion. This combined task reflects real-world clinical workflows where lesion detection, delineation, and diagnosis occur in parallel.

By emphasising both classification and segmentation in a single pipeline, the challenge encourages the development of robust, efficient, and clinically meaningful models suited for automated breast cancer assessment in resource-constrained settings.


🧪 The participants are called to upload their method in a **Cog container** for evaluation (more details under Evaluation)

---

## 📊 Evaluation Criteria

🏁 Performance will be assessed by averaging raw ranks across segmentation and classification metrics. Segmentation will be evaluated using**Normalized Surface Dice (NSD)** and **Lesion-wise Dice Similarity Coefficient (DSC)**[4], while classification will be measured by **Area Under the Curve (AUC)**[5], specificity at 90% sensitivity, and sensitivity at 90% specificity[6]. All metrics will contribute equally to the final ranking.


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
- 💰 Win Cash Prizes: 1st place - 500, 2nd place−300, and 3rd place - 200$
- 🤝 The **top three** contestants/teams will be invited and mentored to submit their winning models to a leading oncology and women's imaging journal.
- 🏥 The **top 2 models** would be deployed for clinical evaluation.
---

## 🗓️ Important Dates

📅 The challenge will run across multiple phases, including training, validation, and test periods.  
Please refer to the timeline below for key dates and deadlines:

![PRECISE-Abreast Timeline](https://github.com/PRECISE-Abreast-Challenge-PAC/PRECISE-ABreast-Challenge/blob/main/Resources/images/TimeLine.jpg.png)

---

## 📨 Submission

Participants will be required to submit predictions for both **Multi-Task Segmentation** and **Multi-Task Classification** tasks.  
The format and naming conventions for the predictions must strictly follow the competition rules.

📜 **Submission Guidelines:**  
Please refer to the [Submission README](https://github.com/PRECISE-Abreast-Challenge-PAC/PRECISE-Abreast-Challenge/blob/main/submission.md) for complete instructions.

---

## 📜 Terms and Conditions
📌 **Terms and conditions apply** please review the full document here:  
[View Full Terms and Conditions](https://github.com/PRECISE-Abreast-Challenge-PAC/PRECISE-Abreast-Challenge/blob/main/terms_conditions.md)

---

## 🧬 Challenge Committees & Contributors

### 👥 Organizing Committee
- Confidence Raymond (SPARK Academy)  
- Moses Iorumbur (FUT Minna, Nigeria)  
- Maruf Adewole (UPenn, US) 
- Henry Sanni (FUT Minna, Nigeria)  
- John Othieno (ECUREI – Uganda)  

### 🛠 Technical Committee
- Mohannad Barakat (FAU, Germany)  
- Noha Magdy (FAU, Germany)  
- Toufiq Musah (KNU Kumasi - Ghana) 
- Oumayma Soula (FMS Sfax - Tunisia)  
- Ayomide Oladele (MAILAB Lagos -Nigeria) 
- Patience Bwire (CWU Rwanda) 

### 🩺 Clinical Committee & Annotators
- Dr. Charity Umoren (MAILAB Lagos – Nigeria)  
- Dr. Abbas Rabiu Muhammad (AKTH Nnewi – Nigeria)  
- Dr. Adaobi Emegoakor (NAUTH Nnewi – Nigeria)  
- Dr. Chinasa Kalaiwo (NK Abuja – Nigeria)  
- Dr. Gbadamosi Yewande Rukayat (LASUTH Lagos – Nigeria)  

### 📊 Data Contributors
- Richard Malumba (ECUREI – Uganda)  
- Denis Musinguzi (ECUREI – Uganda)  
- Patience Atukunda (ECUREI – Uganda)
- Mrs Franca Eze (My Body My Asset Cancer Foundation, Shasha, Lagos)
- Ernest Cook Ultrasound Research and Education Institute (ECUREI), Kampala, Uganda 
- Crestview Radiology Ltd, Lagos, Nigeria / Medical Artificial Intelligence Lab. Lagos, Nigeria

### 🧭 Scientific Directors
- Dr. Udunna Anazodo (McGill University, Canada)  
- Dr. Farouk Dako (University of Pennsylvania, USA)  
- Prof. Michael Kowoya (ECUREI – Uganda) 

### 🤝 Sponsors & Funding
<p align="center">
  <img src="https://github.com/PRECISE-Abreast-Challenge-PAC/PRECISE-ABreast-Challenge/blob/main/Resources/images/LacunaFund.jpg?raw=true" alt="Lacuna Fund" width="120"/>  
  <img src="https://github.com/PRECISE-Abreast-Challenge-PAC/PRECISE-ABreast-Challenge/blob/main/Resources/images/UPenn.jpg?raw=true" alt="Penn Global" width="120"/>
</p>

---

## 📬 Contact

Please contact us for further questions or comments via email:  **preciseabrestchallenge@gmail.com** **https://precisesymposium.org/**

---

## 📚 References

-  [1] Al-Dhabyani, Walid, Mohammed Gomaa, Hussien Khaled, and Aly Fahmy. "Dataset of breast ultrasound images." Data in brief 28 (2020): 104863. 
-  [2]  Pawłowska, A., Ćwierz-Pieńkowska, A., Domalik, A., Jaguś, D., Kasprzak, P., Matkowski, R., Fura, Ł., Nowicki, A., & Zolek, N. A Curated benchmark dataset for ultrasound-based breast lesion analysis. Sci Data 11, 148 (2024). https://doi.org/10.1038/s41597-024-02984-z.  
-  [3] Gómez-Flores, Wilfrido, Maria Julia Gregorio-Calas, and Wagner Coelho de Albuquerque Pereira. "BUS-BRA: A breast ultrasound dataset for assessing computer-aided diagnosis systems." Medical Physics 51, no. 4 (2024): 3110-3123.
-  [4] Zhang E, Seiler S, Chen M, Lu W, Gu X. Boundary-aware semi-supervised deep learning for breast ultrasound computer-aided diagnosis. In 2019 41st Annual International Conference of the IEEE Engineering in Medicine and Biology Society (EMBC) 2019 Jul 23 (pp. 947-950). IEEE.
-  [5] Zhao G, Kong D, Xu X, Hu S, Li Z, Tian J. Deep learning-based classification of breast lesions using dynamic ultrasound video. European Journal of Radiology. 2023 Aug 1;165:110885.
-  [6] Byra M, Galperin M, Ojeda‐Fournier H, Olson L, O'Boyle M, Comstock C, Andre M. Breast mass classification in sonography with transfer learning using a deep convolutional neural network and color conversion. Medical physics. 2019 Feb;46(2):746-55.
