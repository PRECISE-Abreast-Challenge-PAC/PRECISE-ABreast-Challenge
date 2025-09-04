# PRECISE Abreast Ultrasound Segmentation and Classification Challenge (PACE)  
## Final Leaderboard – Test Phase  

This file presents the **final leaderboard results** for the **Test Phase** of the **PRECISE Abreast Ultrasound Segmentation and Classification Challenge (PACE)**.  

The Test Phase was conducted on a hidden dataset, and teams were evaluated on both **segmentation** and **classification** tasks. The final ranking is based on a **composite score** computed from normalized segmentation (DSC, NSD, HD95) and classification (AUC) metrics.  

---

## 🏆 Final Leaderboard  

| Rank | Team ID     | Team Name       | Codabench Username | GitHub Username   | DSC    | NSD    | HD95   | AUC    | N-DSC  | N-NSD  | N-HD95 | N-AUC | Final Score |
|------|-------------|-----------------|-------------------|------------------|--------|--------|--------|--------|--------|--------|--------|-------|-------------|
| 🥇 1st | PACE25_AB008 | EfficientAI    | nimalesh          | Nimalesh         | 0.787  | 0.0101 | 30.45  | 0.242  | 0.934  | 1.000  | 0.997  | 0.358 | **0.823**   |
| 🥈 2nd | PACE25_AB012 | TumorMarker    | leayivor          | TumorMarker      | 0.714  | 0.0089 | 36.91  | 0.356  | 0.795  | 0.873  | 0.836  | 0.642 | **0.786**   |
| 🥉 3rd | PACE25_AB001 | MUSIZ-shiontao | shiontao          | MUSIZ-shiontao   | 0.821  | 0.0071 | 30.35  | 0.205  | 1.000  | 0.673  | 1.000  | 0.264 | **0.734**   |
| 4th  | PACE25_AB007 | crossentropy   | crossentropy      | AgbajeAyomipo    | 0.803  | 0.0099 | 40.97  | 0.182  | 0.964  | 0.987  | 0.735  | 0.208 | 0.723       |
| 5th  | PACE25_AB002 | Tina           | Rehabib           | BiluAilu         | 0.679  | 0.0057 | 45.39  | 0.500  | 0.728  | 0.517  | 0.624  | 1.000 | 0.717       |
| 6th  | PACE25_AB004 | PACE           | Ebimo             | EbimoJohnny      | 0.814  | 0.0061 | 39.41  | 0.273  | 0.986  | 0.563  | 0.774  | 0.434 | 0.689       |
| 7th  | PACE25_AB006 | DeepCure       | veekode           | Victor           | 0.706  | 0.0067 | 42.90  | 0.220  | 0.780  | 0.624  | 0.686  | 0.302 | 0.598       |
| 8th  | PACE25_AB005 | junqiangmler   | junqiangmler      | junqiangchen     | 0.761  | 0.0063 | 54.21  | 0.220  | 0.886  | 0.583  | 0.404  | 0.302 | 0.544       |
| 9th  | PACE25_AB003 | Moyin Labs     | moyinoluwa        | David-Ademola    | 0.738  | 0.0055 | 68.98  | 0.311  | 0.841  | 0.488  | 0.035  | 0.528 | 0.473       |
| 10th | PACE25_AB010 | SAIPAL         | mspratibha        | teamsaipal       | 0.786  | 0.0049 | 64.65  | 0.098  | 0.932  | 0.423  | 0.143  | 0.000 | 0.374       |
| 11th | PACE25_AB011 | Team-GIT-UP    | gamalieladebayo   | TEAM-GIT-UP      | 0.612  | 0.0052 | 70.36  | 0.159  | 0.601  | 0.454  | 0.000  | 0.151 | 0.302       |
| 12th | PACE25_AB009 | vision         | nellie            | Vision677        | 0.297  | 0.0011 | 63.65  | 0.136  | 0.000  | 0.000  | 0.168  | 0.094 | 0.066       |

---

## 📊 Evaluation Metrics  

### 1. Segmentation  
- **Dice Similarity Coefficient (DSC)**  
- **Normalized Surface Dice (NSD)**  
- **95th percentile Hausdorff Distance (HD95)**  

### 2. Classification  
- **Area Under the ROC Curve (AUC)**  

### 3. Normalization Formulas  

For each metric, scores were normalized to [0, 1] across all teams:  

## 📐 Normalization & Scoring Formulas

**Normalized DSC**
$$
N_{\mathrm{DSC}}=\frac{\mathrm{DSC}-\min(\mathrm{DSC})}{\max(\mathrm{DSC})-\min(\mathrm{DSC})}
$$

**Normalized NSD**
$$
N_{\mathrm{NSD}}=\frac{\mathrm{NSD}-\min(\mathrm{NSD})}{\max(\mathrm{NSD})-\min(\mathrm{NSD})}
$$

**Normalized HD95** *(lower is better, so inverted)*
$$
N_{\mathrm{HD95}}=\frac{\max(\mathrm{HD95})-\mathrm{HD95}}{\max(\mathrm{HD95})-\min(\mathrm{HD95})}
$$

**Normalized AUC**
$$
N_{\mathrm{AUC}}=\frac{\mathrm{AUC}-\min(\mathrm{AUC})}{\max(\mathrm{AUC})-\min(\mathrm{AUC})}
$$

**Final Score** *(mean of normalized metrics)*
$$
\mathrm{Final\ Score}=\frac{N_{\mathrm{DSC}}+N_{\mathrm{NSD}}+N_{\mathrm{HD95}}+N_{\mathrm{AUC}}}{4}
$$

---

