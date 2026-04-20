# COMP3314-ML-Challenge

A simple ML image classifier, built for the COMP3314 ML Challenge. 

Due to competition limitations, this ML pipeline does not include any neural network implementations, but only classical ML with feature engineering instead.

---

## Pipeline

The entire pipeline is simple:

1. Load `train.csv` and `test.csv`.
2. Extract fixed wavelet scattering features using `Scattering2D(J=2, shape=(32, 32))`.
3. Fit `StandardScaler` on train features only, then transform train/test.
4. Run PCA.
5. Run optimal classifier search on a stratified subset with `SEARCH_ROWS=12000` and 3-fold CV.
6. Train final models on full training data and apply horizontal-flip TTA on the test set.
7. Fuse the base + TAA scores, select the best model trained, then export to `submission.csv`.

If you want to read more about the specifications and detailed explanations on the pipeline, you can navigate to [report.ipynb](https://github.com/NaughtyChas/COMP3314-ML-Challenge/blob/50c9751ee81d4fe79658a42ab227180335868653/Report.ipynb) or [PDF Report.pdf](https://github.com/NaughtyChas/COMP3314-ML-Challenge/blob/50c9751ee81d4fe79658a42ab227180335868653/PDF%20Report.pdf) for more info.

---

This pipeline has achieved an accuracy up to **0.74950** on the public test set, and **0.75575** on the private test set, ranking \#8 on the leaderboard. 

It is not a top-leaderboard pipeline, but if you're finding something decent, this could be a good one. Better to keep an eye on the [HKU Plagiarism policy](https://tl.hku.hk/plagiarism/) if you're a future student of this course who wants to use this repository as your submission directly.

The used dataset `dataset.zip`, provided by the course staff, is available at the directory `dataset/` for your reference and CI testing. 

---

## Group Members

*Naucha*  
*[REDACTED]*  
*[REDACTED]*  
