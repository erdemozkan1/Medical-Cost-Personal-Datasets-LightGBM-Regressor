
---

# 🏥 Medical Insurance Cost Prediction (LightGBM)

Bu proje, kişisel fiziksel veriler ve yaşam tarzı alışkanlıklarını kullanarak bireylerin sağlık sigortası maliyetlerini (**charges**) tahmin etmek amacıyla geliştirilmiştir. Proje kapsamında veri analizi, özellik mühendisliği, modern Gradient Boosting algoritmaları ve gelişmiş istatistiksel dönüşümler uygulanmıştır.

## 📊 Veri Seti Hakkında
Çalışmada kullanılan veri seti, sigorta maliyetlerini etkileyen 7 temel özniteliği içermektedir:
* **age:** Sigortalının yaşı.
* **sex:** Cinsiyet (Kategorik: 0 = Erkek, 1 = Kadın).
* **bmi:** Vücut kitle indeksi ($kg/m^2$).
* **children:** Sigorta kapsamındaki çocuk/bağımlı sayısı.
* **smoker:** Sigara kullanım durumu (Kategorik: 0 = Hayır, 1 = Evet).
* **region:** İkamet edilen bölge (Southwest, Southeast, Northwest, Northeast).
* **charges:** Sigorta tarafından faturalandırılan yıllık maliyet (**Hedef Değişken**).

## 🛠️ Uygulanan İşlemler ve Metodoloji

### 1. Veri Analizi ve Görselleştirme
* `Seaborn` ve `Matplotlib` kullanılarak değişkenlerin dağılımları incelenmiştir.
* Özellikle **Yaş vs Maliyet** ve **Sigara Kullanımı** arasındaki güçlü korelasyonlar analiz edilmiştir.

### 2. Veri Ön İşleme (Preprocessing)
* **Kategorik Mapping:** `sex` ve `smoker` değişkenleri manuel olarak sayısal değerlere dönüştürülmüştür.
* **One-Hot Encoding:** `region` değişkeni, `ColumnTransformer` kullanılarak modelin anlayabileceği ikili (binary) formatına getirilmiştir.

### 3. Model Eğitimi ve Hiperparametre Optimizasyonu
* **Algoritma:** Yüksek performanslı ve hızlı bir Gradient Boosting kütüphanesi olan **LightGBM (LGBMRegressor)** seçilmiştir.
* **RandomizedSearchCV:** Modelin başarısını artırmak için `learning_rate`, `n_estimators`, `max_depth` ve `num_leaves` gibi parametreler optimize edilmiştir.
* **Box-Cox Dönüşümü:** Hedef değişkenin (`charges`) çarpık dağılımını (skewness) normalleştirmek için Box-Cox dönüşümü uygulanmış, bu sayede hata oranları (MAE) minimize edilmiştir.

## 📈 Model Performansı
Yapılan optimizasyonlar sonucunda elde edilen başarı metrikleri şunlardır:

| Metrik | Değer |
| :--- | :--- |
| **R² Score (Açıklanabilirlik)** | **0.871** |
| **MAE (Ortalama Mutlak Hata)** | **2201.27** |
| **RMSE (Hata Kareler Ort. Kökü)** | **4471.17** |

## 🚀 Başlangıç

### Gereksinimler
Projenin çalışması için aşağıdaki Python kütüphanelerinin yüklü olması gerekir:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn lightgbm scipy
```

### Çalıştırma
```bash
jupyter notebook LightGBMRegressor.ipynb
```

## 🏗️ Kullanılan Teknolojiler
* **Dil:** Python
* **Kütüphaneler:** Scikit-learn, LightGBM, Pandas, NumPy
* **İstatistik:** Scipy (Box-Cox Transformation)
* **Görselleştirme:** Seaborn, Matplotlib

---
**Geliştirici:** Erdem Özkan
