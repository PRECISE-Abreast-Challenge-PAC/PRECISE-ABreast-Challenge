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

## 📚 References

[1] Al-Dhabyani, Walid, Mohammed Gomaa, Hussien Khaled, and Aly Fahmy.  
"Dataset of breast ultrasound images." *Data in Brief* 28 (2020): 104863.

[2] Pawłowska, A., Ćwierz-Pieńkowska, A., Domalik, A., Jaguś, D., Kasprzak, P., Matkowski, R., Fura, Ł., Nowicki, A., & Zolek, N.  
*A Curated benchmark dataset for ultrasound-based breast lesion analysis.* *Scientific Data* 11, 148 (2024).  
https://doi.org/10.1038/s41597-024-02984-z

[3] Gómez-Flores, Wilfrido, Maria Julia Gregorio-Calas, and Wagner Coelho de Albuquerque Pereira.  
"BUS-BRA: A breast ultrasound dataset for assessing computer-aided diagnosis systems." *Medical Physics* 51, no. 4 (2024): 3110–3123.