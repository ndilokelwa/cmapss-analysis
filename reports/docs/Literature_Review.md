# Literature Review

In recent years, predictive maintenance has emerged as a pivotal application of machine learning (ML) and deep learning (DL) in aerospace engineering. As the industry shifts toward smarter and more autonomous operations, Condition-Based Maintenance (CBM) and Prognostics and Health Management (PHM) have gained significant traction. The integration of ML/DL into these paradigms enables early fault detection, accurate Remaining Useful Life (RUL) estimation, and dynamic maintenance scheduling, ultimately improving reliability and reducing operational costs.

Predictive maintenance models typically fall into three categories: RUL estimation, classification (healthy/faulty), and fault prediction. Several ML algorithms—such as Random Forest (RF), Support Vector Machines (SVM), Gradient Boosting, and k-Nearest Neighbors (KNN)—as well as DL methods like Convolutional Neural Networks (CNNs), Long Short-Term Memory (LSTM) networks, and autoencoders have been successfully employed for these tasks. The study by Saxena et al. [1] generating the C-MAPSS dataset for aircraft engines remains one of the foundational works in this field, setting benchmarks for RUL prediction tasks. Later, Gupta et al. [2] showed that Random Forest Regression (RFR) outperformed other classical ML models in both regression and classification scenarios. Similarly, Muneer et al. [3] found attention-based deep convolutional neural network (DCNN) to be superior in modeling temporal dependencies, making them especially suitable for time-series degradation signals.

Despite these advances, accurate evaluation and comparison of models remain challenging. Performance metrics vary according to task type: regression tasks often use Root Mean Squared Error (RMSE), Mean Absolute Error (MAE), or R-squared (R²), while classification tasks rely on metrics like accuracy, precision, recall, F1-score, and Area Under the Curve (AUC). However, few studies standardize these metrics across experiments, making it difficult to objectively compare models.

Recent literature also highlights the importance of feature extraction and sensor fusion in improving model accuracy. Wei et al. [4] explored a multi-sensor data fusion approach, combining data from vibration, and temperature sensors. They found that sensor fusion is capable of outperforming the preliminary decisions made by individual sensors in terms of both prediction
accuracy and variance in predictions. Similarly, Gawde et al. [5] showed that multi-sensor data fusion significantly outperforms single-sensor approaches, demonstrating an enhancement in fault prediction accuracy.

An emerging research trend involves the use of physics-informed or hybrid models that combine physics-informed with data-driven approaches. These models can improve generalizability and offer physical interpretability, which purely data-driven approaches often lack. In the aerospace domain, where safety and accountability are paramount, such hybrid approaches may be more acceptable to regulators and engineers.

Another critical challenge lies in model interpretability. While DL models often outperform classical ML methods in accuracy, their black-box nature limits their adoption in safety-critical industries like aerospace. To address this, Explainable AI (XAI) techniques are being explored. Ribeiro et al. [6] introduced LIME (Local Interpretable Model-agnostic Explanations), and Lundberg et al. [7] developed SHAP (SHapley Additive exPlanations), both of which aim to interpret model predictions locally and globally. While these tools are promising, their application in RUL prediction and fault diagnosis remains underexplored, particularly in models involving sensor fusion and temporal data.

A growing body of work also explores integrating attention mechanisms into DL models to identify the most critical time steps or sensor channels for prediction. Boujamza and Elhaq [8] proposed an attention-based LSTM network, improving both interpretability and accuracy in turbofan engine degradation modeling. However, few studies compare these attention-based models with traditional XAI frameworks like SHAP or LIME in terms of human interpretability and operational integration.

Additionally, data scarcity and imbalance continue to pose significant hurdles, especially when dealing with rare failure modes. Data augmentation techniques, semi-supervised learning, and transfer learning have been suggested as potential solutions, but consistent benchmarking is still lacking.

## Conclusion
In summary, ML and DL methods have shown considerable promise for predictive maintenance in aerospace systems, particularly for tasks like RUL estimation and fault detection. While performance metrics indicate high accuracy, challenges remain in terms of interpretability, data quality, and model generalization. Emerging techniques such as sensor fusion, hybrid modeling, and XAI tools offer promising solutions but require further research and standardized evaluation. Bridging the gap between model accuracy and explainability is crucial for real-world deployment, especially in high-stakes environments where transparency and safety are non-negotiable. Future work should focus on developing interpretable, physics-informed DL models, validated on realistic datasets, and evaluated through consistent, domain-specific metrics.

## Reference

[1] A. Saxena, K. Goebel, D. Simon and N. Eklund, "Damage propagation modeling for aircraft engine run-to-failure simulation," *2008 International Conference on Prognostics and Health Management*, Denver, CO, USA, 2008, pp. 1-9, https://doi.org/10.1109/PHM.2008.4711414.

[2] Gupta, R. K., Nakum, J., Gupta, P., "A Machine Learning Approach for Turbofan Jet Engine Predictive Maintenance", *Procedia Computer Science*, Volume 259, 2025, Pages 161-171, ISSN 1877-0509, https://doi.org/10.1016/j.procs.2025.03.317.


[3] Muneer, A., Taib, S. M., Fati, S. M., & Alhussian, H. (2021). "Deep-Learning Based Prognosis Approach for Remaining Useful Life Prediction of Turbofan Engine". *Symmetry*, 13(10), 1861. https://doi.org/10.3390/sym13101861

[4] Y. Wei, D. Wu and J. Terpenny, "Decision-Level Data Fusion in Quality Control and Predictive Maintenance," *IEEE Transactions on Automation Science and Engineering*, vol. 18, no. 1, pp. 184-194, Jan. 2021, https://doi.org/10.1109/TASE.2020.2964998.

[5] Gawde, S., Patil, S., Kumar, S., Kamat, P., Kotecha, K., "An explainable predictive maintenance strategy for multi-fault diagnosis of rotating machines using multi-sensor data fusion", *Decision Analytics Journal*, Volume 10, 2024, 100425, ISSN 2772-6622, https://doi.org/10.1016/j.dajour.2024.100425.

[6] Ribeiro, M. T., Singh, S., & Guestrin, C. (2016). “Why should I trust you?”: Explaining the predictions of any classifier. *In Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining* (pp. 1135–1144). https://doi.org/10.1145/2939672.2939778

[7] Lundberg, S. M., and  Lee, S.-I. (2017). A unified approach to interpreting model predictions. In Proceedings of the 31st International Conference on Neural Information Processing Systems (NIPS 2017), 4765–4774. 
https://doi.org/10.48550/arXiv.1705.07874

[8] Boujamza, A., Elhaq, S. L., "Attention-based LSTM for Remaining Useful Life Estimation of Aircraft Engines", *IFAC-PapersOnLine*, Volume 55, Issue 12, 2022, Pages 450-455, ISSN 2405-8963, https://doi.org/10.1016/j.ifacol.2022.07.353.