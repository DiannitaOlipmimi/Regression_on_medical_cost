# REGRESI LINIER DAN ASUMSINYA

## 📌Table of contents
- [Definisi](https://github.com/DiannitaOlipmimi/regresi_dan_asumsinya#definition)
- [Study Case](https://github.com/DiannitaOlipmimi/regresi_linier#study-case)
- [Step by Step analysis](https://github.com/DiannitaOlipmimi/regresi_dan_asumsinya#step-by-step-analysis)
- [Result](https://github.com/DiannitaOlipmimi/regresi_dan_asumsinya#step-by-step-analysis)
- [Dataset](https://github.com/DiannitaOlipmimi/regresi_dan_asumsinya#step-by-step-analysis)
- [Links](https://github.com/DiannitaOlipmimi/regresi_dan_asumsinya#step-by-step-analysis)

## 📌**Definisi**

### 📒Analisis Regresi Linier
Analisis regresi linier merupakan analisis yang digunakan untuk melihat hubungan dua variabel yang diasumsikan memiliki hubungan yang linier (bergaris lurus). regresi linier terbagi menjadi dua, yaitu:
1. regresi linier sederhana (*simple linear regression*)
2. regresi linier berganda (*multiple linear regression*)

### 📒Uji Asumsi dalam Regresi Linier
dikarenakan regresi linier merupakan metode yang memiliki asumsi pada variabel-variabelnya memiliki hubungan yang linier, maka diperlukan pengujian asumsi untuk membuktikan kevalidannya. uji asumsi yang dilakukan pada regresi linier antara lain:
- uji asumsi kenormalan residual
- uji asumsi kebebasan residual
- uji asumsi kehomogenan variansi residual
- uji asumsi ketiadaan multikolinieritas dalam variabel prediktor X dengan jumlah lebih dari 2

### 📒Evaluasi Model Regresi Linier
ketepatan hasil regresi linier dapat diketahui dengan menggunakan:
1. koefisien determinasi (*R squared*)
2. Uji F dari tabel ANOVA
3. uji T pada variabel independennya

## 📌**Study Case**
### **Memprediksi Harga Rumah Menggunakan Regresi Linier Berganda**

### 📒 Deskripsi Masalah:
Ask a home buyer to describe their dream house, and they probably won't begin with the height of the basement ceiling or the proximity to an east-west railroad. But this playground competition's dataset proves that much more influences price negotiations than the number of bedrooms or a white-picket fence.

With 79 explanatory variables describing (almost) every aspect of residential homes in Ames, Iowa, this competition challenges you to predict the final price of each home.

### 📒 Data dan Variabel:
- `SalePrice`: the property's sale price in dollars. This is the target variable that you're trying to predict.
- `MSSubClass: The building class
- `LotArea: Lot size in square feet
- `Neighborhood: Physical locations within Ames city limits
- `HouseStyle: Style of dwelling
- `OverallQual: Overall material and finish quality
- `OverallCond: Overall condition rating
- `YearBuilt: Original construction date
- `RoofStyle: Type of roof
- `ExterQual: Exterior material quality
- `BsmtQual: Height of the basement
TotalBsmtSF: Total square feet of basement area
CentralAir: Central air conditioning
Electrical: Electrical system
GrLivArea: Above grade (ground) living area square feet
FullBath: Full bathrooms above grade
Bedroom: Number of bedrooms above basement level
Kitchen: Number of kitchens
TotRmsAbvGrd: Total rooms above grade (does not include bathrooms)
Fireplaces: Number of fireplaces
GarageCars: Size of garage in car capacity
GarageArea: Size of garage in square feet
PoolArea: Pool area in square feet
MoSold: Month Sold
YrSold: Year Sold
SaleType: Type of sale
SaleCondition: Condition of sale

### 📒 Tujuan:
membuat model regresi yang dapat memprediksi harga penjualan rumah berdasarkan variabel yang ada

### 📒 Langkah Analisis:
✅ *Exploratory Data Analysis* (EDA):
1. Melakukan pengecekan apakah terdapat missing data, duplicate data, dan error data
2. Mengubah data kategorik menjadi ata numerik apabila diperlukan
3. Melakukan deskriptif statistik pada data (melihat rata-rata, median, dan nilai lainnya)
4. Memvisualisasikan data untuk melihat pola data
5. Melihat adanya outlier menggunakan boxplot
6. Mencari hubungan antar variabel menggunakan scatter plot

✅ Analisis:
1. Membuat model regresi linier berganda
2. Membuat hasil ulang menggunakan model

✅ Evaluasi:
1. Melakukan pengujian secara overall dan parsial
2. Melakukan pengujian asumsi 
3. Melihat hasil kecocokan model menggunakan indikator seperi R-Squared, RMSE, dll.
4. Visualisasi data awal dengan data hasil model
5. Melakukan percobaan dengan dummy variable

## 📌**Step by step analysis**
### 📒 **menggunakan Excel**
1. menginstall add-ins **Data Analysis ToolPak** pada Excel 
[Tutorial dari Microsoft](https://support.microsoft.com/en-gb/office/load-the-analysis-toolpak-in-excel-6a63e598-cd6d-42e3-9317-6b40ba1a66b4)
2. membuka tab Data pada excel > Ribbon Analysis > memilih menu Data Analysis
3. memilih Regression sebagai analysis tools dan mengisi value cell sesuai dengan perintah dialog box

### 📒 **menggunakan R/RStudio**
- membuat model
```r
regresi=lm(y~x1+x2+x3+x4+x5, data = data)
summary(regresi)
hasil=summary(regresi)
```

- menguji asumsi
```r
#uji normalitas-kolmogorov-smirnov
library(nortest)
lillie.test(regresi$residuals)

#durbin-watson untuk uji auotokorelasi
library(lmtest)
dwtest(regresi)

#uji heterokedastisitas dengan Breusch Pagan test
library(lmtest)
bptest(regresi, studentize = FALSE, data=data)

#uji multiko
library(car)
vif(regresi)
```

### 📒**menggunakan Python**
Google colab
https://colab.research.google.com/drive/1jeNXk2dnevsDgpS5lBgTOu0HKH68HpaV?usp=sharing

```python
regr = linear_model.LinearRegression()
regr.fit(X, y)

print('Intercept: \n', regr.intercept_)
print('Coefficients: \n', regr.coef_)

x = sm.add_constant(X)

model = sm.OLS(y, X).fit()
predictions = model.predict(X)

print_model = model.summary()
print(print_model)
```

## 📌**Result**
### 📒**menggunakan Excel**
![Alt text](<images/Regresi Excel 1.png>)
![Alt text](<images/Regresi Excel 2.png>)

### 📒**menggunakan R/RStudio**

### 📒**menggunakan Python**

## 📌**Dataset**
### **Housing Prices (5 data teratas)**
|price|area|bedrooms|bathrooms|stories|mainroad|guestroom|basement|hotwaterheating|airconditioning|parking|prefarea|furnishingstatus|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|13300000|7420|4|2|3|yes|no|no|no|yes|2|yes|furnished|
|12250000|8960|4|4|4|yes|no|no|no|yes|3|no|furnished|
|12250000|9960|3|2|2|yes|no|yes|no|no|2|yes|semi-furnished|
|12215000|7500|4|2|2|yes|no|yes|no|yes|3|yes|furnished|
|11410000|7420|4|1|2|yes|yes|yes|no|yes|2|no|furnished|



## 📌**Links**
https://www.analyticsvidhya.com/blog/2021/10/everything-you-need-to-know-about-linear-regression/

https://www.kaggle.com/datasets/yasserh/housing-prices-dataset 

https://support.microsoft.com/en-gb/office/load-the-analysis-toolpak-in-excel-6a63e598-cd6d-42e3-9317-6b40ba1a66b4