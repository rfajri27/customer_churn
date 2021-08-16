# Customer Churn Prediction using Machine Learning

Dataset yang digunakan pada project ini merupakan dataset  **DQLab Telco**  dari salah satu modul project-based yang telah saya selesaikan di DQLab Academy.

## Data Cleansing
Langkah-langkah yang akan dilakukan adalah:
- Memfilter customerID (Nomor telphone) yang tidak valid dan menghilangkan duplikasi
- Mengatasi data-data yang memiliki *missing values* dengan metode *dropping* dan *imputation*
- Mengatasi outlier atau pencilan dengan menggunakan metode *interquartile range* (IQR)
- Menstandarisasi nilai dari variable

## Exploratory Data Analysis
### Percentege of Churn Customer

![](images/churn_percentege.png)

Berdasarkan plot tersebut dapat kita ketahui bahwa dari keseluruhan customer terdapat 26.4% customer yang melakukan *churn*.

### Exploring Numerical Columns

![](images/numerical_plot.png)

- Berdasarkan plot `MonthlyCharges` dapat kita ketahui bahwa semakin kecil biaya bulanan yang dikenakan, semakin kecil juga kecenderungan untuk melakukan *churn*
- Berdasarkan plot `TotalCharges` dapat dilihat bahwa tidak ada kecenderungan apapun terhadap *churn*
- Berdasarkan plot `tenure` dapat kita ketahui bahwa ada kecenderungan semakin lama berlangganan, semakin kecil kecenderungan untuk melakukan *churn*

### Exploring Categorical Columns

![](images/categorical_plot.png)

- Tidak ada perbedaan signifikan untuk melakukan *churn* jika dilihat faktor jenis kelamin (`gender`) dan layanan telfonnya (`PhoneSevice`)
- Ada kecenderungan melakukan *churn* untuk customer dengan kategori berikut:
    * Tidak memiliki partner (partner: No)
    * orang-orang yang statusnya adalah senior citizen (`SeniorCitizen: Yes`)
    * orang-orang yang mempunyai layanan streaming TV (`StreamingTV: Yes`)
    * orang-orang yang mempunyai layanan Internet (`internetService: Yes`)
    * orang-orang yang tagihannya paperless (`PaperlessBilling: Yes`)

## Data PreProcessing
- Menghapus columns yang tidak dibutuhkan dalam pembuatan model
- Melakukan encoding data untuk categorical data
- Mebagi dataset menjadi 70% data training dan 30% data testing

## Modeling
### Model: Logistic Regression

```
{
	Classification Report Logistic Regression Model :
              precision    recall  f1-score   support

           0       0.85      0.90      0.87      1539
           1       0.66      0.54      0.60       546

    accuracy                           0.81      2085
   macro avg       0.75      0.72      0.74      2085
weighted avg       0.80      0.81      0.80      2085
}
```

![](images/snf_log_model.png)

### Model: Random Forest Classifier

```
{
	Classification Report Random Forest Classifier:
              precision    recall  f1-score   support

           0       0.83      0.91      0.87      1539
           1       0.65      0.48      0.55       546

    accuracy                           0.80      2085
   macro avg       0.74      0.69      0.71      2085
weighted avg       0.78      0.80      0.79      2085

}
```

![](images/snf_cnf_model.png)

### Model: Gradient Boosting Classifier

```
{
	Classification Report Gradient Boosting Classifier:
              precision    recall  f1-score   support

           0       0.84      0.91      0.88      1539
           1       0.68      0.51      0.59       546

    accuracy                           0.81      2085
   macro avg       0.76      0.71      0.73      2085
weighted avg       0.80      0.81      0.80      2085
}
```

![](images/snf_gbt_model.png)
