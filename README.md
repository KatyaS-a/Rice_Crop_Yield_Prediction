# Rice_Crop_Yield_Prediction
![rice-arroz-scaled 2](https://github.com/user-attachments/assets/627d6964-882a-44bd-95ac-8bab293fba65)

The goal of this project is to find insights on predicting crop yields of rice in India. Smallholder farmers, who make up most of the workforce there, face challenges like poverty and malnutrition. Predictive insights can help them make better decisions about resource use, and help in supporting food security.

The **dataset** can be found on [Kaggle](https://www.kaggle.com/datasets/sudhanshu2198/crop-yield-prediction-hachathon/data). The data is from 2022 and includes 43 features related to farming practices, fertilizer use, and crop cycle dates. 

We used a **CatBoost regression** model, which works well with complex data. Our model achieved a *Mean Absolute Error* of 192 and an *R-squared* score of 0.67, meaning it explains about 67% of the variation in crop yields. This provides a reasonably accurate prediction but still leaves room for improvement.
****

## Interpreting the model
To understand our model’s predictions, we used interpretability tools, LIME and SHAP. LIME helps us understand why the model made a specific prediction, which can help farmers understand why a certain yield is predicted for their specific plot. SHAP, on the other hand, gives a more general view of which attributes are consistently important for predicting yield across all data.  

### LIME
<img width="968" alt="Screenshot 2024-11-15 at 1 33 57 PM" src="https://github.com/user-attachments/assets/ebca2dc3-8df5-49a8-a8e7-37c19f4603a1">

**Predicted Value**: The model predicted a value of 2139.02 for this particular instance. LIME provides a range (960.63 to 2560.52) based on the perturbations it created to test the feature contributions.  

**Positive and Negative Contributions**:
- **Positive** (Orange): Features that push the prediction value higher. For instance: onehot__MineralFertAppMethod_SoilApplied and onehot__CropEstMethod_Manual_PuddledLine both contribute positively to the prediction, adding 71.72 and 48.40 units, respectively. scaler__2appDaysUrea contributes 29.96 units to the prediction.
- **Negative** (Blue): Features that pull the prediction value down. For example: onehot__District_Vaishali has a large negative impact, reducing the prediction by 143.09. onehot__PCropSolidOrgFertAppMethod_SoilApplied reduces it by 44.39.
- 
**Feature Values**: On the right, each feature’s value is shown for this specific instance. For example, onehot__District_Vaishali has a value of 1.0 (indicating this instance is in the district of Vaishali), and scaler__BasalUrea has a value of -0.24.

***
  ### SHAP
<img width="1022" alt="Screenshot 2024-11-15 at 1 41 29 PM" src="https://github.com/user-attachments/assets/8a46a873-d7a8-44a5-b2e8-bf5e35a6329d">

The baseline here is zero, representing the average starting point of the prediction. Each feature then either adds to or subtracts from this baseline.
Positive contributions are shown in red, they increase yields. For example, 'Mineral Fertilizer Application by ’soil adds 0.23 on average, confirming its effectiveness. 
Negative contributions are shown in blue, they reduce yields.

****
## Recommendations  

Based on these insights, we can recommend promoting effective fertilizer methods, especially mineral soil applications. We can also suggest targeted support for regions like Vaishali that face challenges. Finally, educating farmers on specific land preparation methods can also boost productivity. By sharing these findings, we can help farmers make better-informed decisions for sustainable farming.

