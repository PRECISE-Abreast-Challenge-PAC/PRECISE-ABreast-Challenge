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

## 📚 References

[1] Al-Dhabyani, Walid, Mohammed Gomaa, Hussien Khaled, and Aly Fahmy.  
"Dataset of breast ultrasound images." *Data in Brief* 28 (2020): 104863.

[2] Pawłowska, A., Ćwierz-Pieńkowska, A., Domalik, A., Jaguś, D., Kasprzak, P., Matkowski, R., Fura, Ł., Nowicki, A., & Zolek, N.  
*A Curated benchmark dataset for ultrasound-based breast lesion analysis.* *Scientific Data* 11, 148 (2024).  
https://doi.org/10.1038/s41597-024-02984-z

[3] Gómez-Flores, Wilfrido, Maria Julia Gregorio-Calas, and Wagner Coelho de Albuquerque Pereira.  
"BUS-BRA: A breast ultrasound dataset for assessing computer-aided diagnosis systems." *Medical Physics* 51, no. 4 (2024): 3110–3123.