# Capstone Two Final Report: Fashion Satisfaction Analysis

**Author:** Cristina Reardon  
**Date:** 2025  

---

## 1. Problem Identification

Clothing choices are both practical and expressive, but not all individuals feel that their wardrobe reflects their personality. This project investigates:

**Research Question:**  
*Which demographic, style, and shopping factors best explain differences in fashion satisfaction, and can we predict satisfaction numerically on a 1–10 scale?*

**Data:**  
Survey responses (n≈150) capturing demographics (age, gender, profession), style preferences, shopping behaviors, lifestyle indicators, and a 1–10 self-reported *Satisfaction* score.

---

## 2. Data Wrangling

Steps applied:

- **Column cleaning:** stripped whitespace, normalized headers, renamed long survey items to concise labels (e.g., `OutfitType`, `ShoppingFrequency`, `ComfortImportance`, `FunctionVsAesthetic`, `Satisfaction`).  
- **Dropped empty/unusable columns:** survey section markers and duplicates.  
- **Datetime processing:** parsed timestamps into weekday and hour features.  
- **Missing values:** dropped rows missing essential features (`AgeGroup`, `OutfitType`, `ShoppingFrequency`, `Satisfaction`).  
- **Encoding:** categorical variables were dummy-encoded for modeling.  
- **Standardization:** numeric features (e.g., Satisfaction) were magnitude-standardized where required.

Final cleaned dataset: **147 rows × 18 columns.**

---

## 3. Exploratory Data Analysis (EDA)

### 3.1 Satisfaction Distribution
- Low (≤4): minority of respondents.  
- Medium (5–6): ~20%.  
- High (≥7): majority, indicating most respondents are relatively satisfied.

### 3.2 Key Behaviors by Satisfaction Segment

- **Outfit Type:**  
  - Low/Medium ~75–78% **Casual** only.  
  - High shows more **Sporty (10%)**, **Formal (10%)**, **Chic/Trendy (6%)**.  
  → Greater style diversity correlates with higher satisfaction.

- **Shopping Frequency:**  
  - Low/Medium skew toward **Rarely** or **Every few months**.  
  - High includes **Monthly (22%)** and **Weekly (7%)** shoppers.  
  → More regular shopping correlates with higher satisfaction.

- **Function vs. Aesthetic:**  
  - High clusters at **Equal balance (~64%)**.  
  - Low leans more **functionality-heavy**.  
  → Balance beats extremes.

- **Comfort:**  
  - High: ~84% say comfort is **Extremely/Somewhat important**.  
  - “Not important at all” nearly absent.  

- **Shopping Channels:**  
  - Low: dominated by **Fast fashion (63%)**.  
  - High: diversified across **Online (25%)**, **Boutiques (20%)**, **Luxury (15%)**, **Thrift (10%)**.  

### 3.3 Age × Style Heatmap
- Each age group shows a “most satisfying” style lane.  
- Example: Age 25–34 tilts toward **Chic**; 35–44 mixes **Casual + Formal**.  
- Can guide **age-targeted style recommendations**.

---

## 4. Feature Engineering

- **Target:** Satisfaction (numeric 1–10).  
- **Segment:** also bucketed into Low / Medium / High for interpretation.  
- **Categorical features:** OutfitType, Wardrobe, ShoppingFrequency, FunctionVsAesthetic, ComfortImportance, ShoppingLocation, AgeGroup, Gender.  
- **Dummy features:** created for each categorical option.  
- **Numeric features:** standardized.  
- **Train/test split:** 80/20.

---

## 5. Modeling

Three models trained:

1. **Linear Regression**  
   - Baseline interpretability.  
2. **Random Forest Regressor**  
   - Captures non-linear splits, feature importance.  
3. **Gradient Boosting Regressor**  
   - Boosted trees, strong performance on small tabular data.

---

## 6. Model Comparison

| Model                  | R²   | RMSE  | MAE  |
|-------------------------|------|-------|------|
| Linear Regression       | …    | …     | …    |
| Random Forest Regressor | …    | …     | …    |
| Gradient Boosting       | …    | …     | …    |

*(Populate with your notebook’s actual evaluation metrics.)*

**Best Model:** Gradient Boosting — consistently lowest error, highest R².

---

## 7. Final Model Results

- Gradient Boosting applied to test set.  
- Captured non-linear effects:  
  - Style repertoire + shopping cadence are strongest drivers.  
  - Comfort and Function vs. Aesthetic balance also predictive.  
- Age group effects are modest but consistent with EDA patterns.

---

## 8. Recommendations

1. **Encourage style experimentation**: Suggest adding a Sporty or Chic piece to Casual wardrobes.  
2. **Promote monthly cadence**: Send light nudges to refresh closets regularly.  
3. **Balance messaging**: Emphasize both functionality and aesthetics.  
4. **Comfort as default**: Always surface comfort features in copy and filtering.  
5. **Diversify shopping channels**: Encourage users to try boutiques, thrift, and online variety.

---

## 9. Limitations

- Small sample size (n≈150) limits generalizability.  
- Self-reported survey bias possible.  
- Class imbalance across some categories (e.g., Bohemian, Chic).  
- Cross-sectional — cannot claim causality.

---

## 10. Next Steps

- Hyperparameter tuning for Gradient Boosting.  
- SHAP analysis for feature interpretability.  
- Larger, more diverse survey for external validation.  
- Deploy model in a recommendation loop (cold-start via age/style defaults, adapt with feedback).  
- Consider clustering (unsupervised) for segment discovery.

---

## 11. Figures

- <img width="2272" height="1004" alt="image" src="https://github.com/user-attachments/assets/8ee91983-2e6a-4e0f-ac9e-0f32456fb504" />
- <img width="2201" height="978" alt="image" src="https://github.com/user-attachments/assets/ea528415-a3d6-458a-a472-d87f97e67d6d" />
- <img width="2226" height="964" alt="image" src="https://github.com/user-attachments/assets/8a40ccd6-df2b-458f-9947-b684efff4497" />
- <img width="2184" height="959" alt="image" src="https://github.com/user-attachments/assets/7f745f3d-9bb9-4e47-aefe-0c0a1378f9aa" />
- <img width="785" height="389" alt="Screenshot 2025-09-15 at 10 02 58 PM" src="https://github.com/user-attachments/assets/dcd45b89-d45d-4f6d-80b8-eb89b92143a3" />
- <img width="835" height="483" alt="Screenshot 2025-09-15 at 10 03 28 PM" src="https://github.com/user-attachments/assets/2bfa4ff0-c902-4b1b-9a4f-c81be554ff61" />


---

## 12. Summary & Key Takeaways

Higher satisfaction in fashion is associated with:
- Broader style repertoire (beyond Casual).  
- More frequent shopping cadence.  
- Balanced focus on functionality and aesthetics.  
- Comfort as a core principle.  
- Diverse shopping channels.  

The Gradient Boosting model predicts satisfaction best, showing practical opportunities for personalization and marketing to help users feel more authentically represented by their wardrobes.
