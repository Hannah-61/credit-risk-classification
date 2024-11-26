# Credit Risk Classification Report

## Overview of the Analysis

The purpose of this analysis was to evaluate the creditworthiness of borrowers using historical data from a peer-to-peer lending service. Specifically, the goal was to predict whether a loan is "healthy" (0) or "high-risk" (1) using a logistic regression model.

### Key Data Details:

* **Features (X):** Loan size, interest rate, borrower income, debt-to-income ratio, number of accounts, derogatory marks, and total debt.
* **Label (y):** `loan_status`:
  * `0`: Healthy loan.
  * `1`: High-risk loan.
* The dataset was split into training and testing sets for model development and evaluation.

### Stages of the Analysis:

1. **Data Preparation:** The dataset was loaded, and features (`X`) and labels (`y`) were extracted.
2. **Data Splitting:** The data was split into training and testing subsets using a 75-25% split with a random seed of 1 to ensure reproducibility.
3. **Model Training:** A logistic regression model was trained on the training data (`X_train`, `y_train`).
4. **Model Evaluation:** The model's performance was evaluated using a confusion matrix and a classification report.

---

## Results

### Logistic Regression Model Performance:

* **Confusion Matrix:**

  <pre class="!overflow-visible"><div class="contain-inline-size rounded-md border-[0.5px] border-token-border-medium relative bg-token-sidebar-surface-primary dark:bg-gray-950"><div class="flex items-center text-token-text-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md h-9 bg-token-sidebar-surface-primary dark:bg-token-main-surface-secondary select-none">lua</div><div class="sticky top-9 md:top-[5.75rem]"><div class="absolute bottom-0 right-2 flex h-9 items-center"><div class="flex items-center rounded bg-token-sidebar-surface-primary px-2 font-sans text-xs text-token-text-secondary dark:bg-token-main-surface-secondary"><span class="" data-state="closed"><button class="flex gap-1 items-center select-none py-1"><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="icon-sm"><path fill-rule="evenodd" clip-rule="evenodd" d="M7 5C7 3.34315 8.34315 2 10 2H19C20.6569 2 22 3.34315 22 5V14C22 15.6569 20.6569 17 19 17H17V19C17 20.6569 15.6569 22 14 22H5C3.34315 22 2 20.6569 2 19V10C2 8.34315 3.34315 7 5 7H7V5ZM9 7H14C15.6569 7 17 8.34315 17 10V15H19C19.5523 15 20 14.5523 20 14V5C20 4.44772 19.5523 4 19 4H10C9.44772 4 9 4.44772 9 5V7ZM5 9C4.44772 9 4 9.44772 4 10V19C4 19.5523 4.44772 20 5 20H14C14.5523 20 15 19.5523 15 19V10C15 9.44772 14.5523 9 14 9H5Z" fill="currentColor"></path></svg>Copy code</button></span></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-lua">[[18655,  110],
   [   36,  583]]
  </code></div></div></pre>

  * True negatives (healthy loans correctly classified): 18,655
  * False positives (healthy loans classified as high-risk): 110
  * True positives (high-risk loans correctly classified): 583
  * False negatives (high-risk loans classified as healthy): 36
* **Classification Report:**

  | Metric    | Healthy Loan (`0`) | High-Risk Loan (`1`) | Overall Accuracy |
  | --------- | -------------------- | ---------------------- | ---------------- |
  | Precision | 100%                 | 84%                    | 99%              |
  | Recall    | 99%                  | 94%                    |                  |
  | F1-Score  | 100%                 | 89%                    |                  |
  | Support   | 18,765               | 619                    |                  |

### Key Observations:

* The model performs exceptionally well for predicting healthy loans (`0`), achieving near-perfect precision, recall, and F1-scores.
* The high-risk loans (`1`) are also well-predicted, though precision is slightly lower (84%), indicating some healthy loans are being misclassified as high-risk.
* The recall for high-risk loans is strong at 94%, meaning the model identifies most high-risk loans correctly.

---

## Summary

### Model Performance:

The logistic regression model demonstrates strong performance overall, with an accuracy of 99%. The F1-score for both healthy loans (`0`) and high-risk loans (`1`) is high, indicating the model balances precision and recall effectively.

### Recommendations:

* **Recommendation:** The model is suitable for use in production, especially if the primary goal is to minimize false negatives (i.e., misclassifying high-risk loans as healthy). Its high recall for high-risk loans ensures most risky borrowers are identified.
* **Considerations:**
  * If misclassifying healthy loans as high-risk is a significant concern, further model optimization or data resampling could help.
  * Additional models like Random Forest or Gradient Boosting could be explored for potentially better handling of class imbalances.
