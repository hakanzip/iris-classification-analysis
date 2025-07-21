# Iris Çiçek Türü Sınıflandırması

Bu proje, klasik Iris çiçek veri seti üzerinde sınıflandırma ve görselleştirme uygulamalarını içermektedir. Temel hedef; Iris çiçeklerinin fiziksel özelliklerinden yola çıkarak türlerini doğru şekilde sınıflandırabilen makine öğrenmesi modelleri geliştirmek, aynı zamanda veri görselleştirme teknikleriyle analizleri desteklemektir.

## 📁 Klasör Yapısı

```
├── data/
│   └── Iris.csv                      # Orijinal veri seti
├── images/
│   ├── correlation_heatmap.png
│   ├── kmeans_clustering.png
│   ├── pairplot_species.png
│   ├── petal_length_histogram.png
│   ├── scatter_matrix.png
│   ├── sepal_length_boxplot.png
│   └── species_distribution.png
├── notebook/
│   └── saksuka_ırıs.ipynb            # Ana Jupyter Notebook
├── requirements.txt
└── README.md                         # Bu dökümantasyon
```

## 🔗 Veri Seti

- **Kaynak:** [UCI Machine Learning Repository - Iris Data Set (Kaggle mirror)](https://www.kaggle.com/datasets/uciml/iris)
- **Gözlem Sayısı:** 150
- **Özellikler:** `SepalLengthCm`, `SepalWidthCm`, `PetalLengthCm`, `PetalWidthCm`
- **Hedef Değişken:** `Species` (Setosa, Versicolor, Virginica)
- **Eksik Veri:** Yok
- **ID Kolonu:** Modelleme dışında bırakıldı.

## ⚙️ Kullanılan Kütüphaneler

```txt
pandas
numpy
matplotlib
seaborn
scikit-learn
xgboost
```

Kurulum için:
```bash
pip install -r requirements.txt
```

## 🔍 Adım Adım Yöntem

1. **Veri Yükleme ve İnceleme**
   - `df.info()` ile veri yapısı incelendi.
   - ID kolonu çıkarıldı, `Species` etiketleri `LabelEncoder` ile sayısallaştırıldı.

2. **EDA - Keşifsel Veri Analizi**
   - `species_distribution.png`: Tür dağılımı dengeli.
   - `pairplot_species.png`: Türler arasında belirgin ayrım gözlemleniyor.
   - `correlation_heatmap.png`: Petal boyutları yüksek korelasyon gösteriyor.
   - `scatter_matrix.png`, `sepal_length_boxplot.png`, `petal_length_histogram.png`: Detaylı veri dağılımı ve uç değer incelemeleri yapıldı.

3. **Önişleme**
   - `StandardScaler` ile sayısal veriler standartlaştırıldı.
   - Hedef değişken: `LabelEncoder` ile 0–1–2 olarak etiketlendi.

4. **Modelleme**
   - **Logistic Regression:** `C` ve `penalty` için `GridSearchCV` uygulandı.
   - **Random Forest Classifier:** `n_estimators`, `max_depth` parametreleri arandı.
   - **Support Vector Machine (SVC):** Çekirdek tipi ve `C` üzerinden tarama yapıldı.
   - **XGBoost Classifier:** Hızlı ve etkili sınıflandırma için denendi.

5. **Model Değerlendirme**
   - `cross_val_score` ile 5-fold çapraz doğrulama
   - `accuracy_score`, `precision_score`, `recall_score`, `f1_score`, `confusion_matrix` hesaplandı.
   - `classification_report` ile her modelin sınıflara göre başarısı ölçüldü.

6. **Kümeleme (K-Means)**
   - `kmeans_clustering.png`: Gözetimsiz öğrenme ile 3 grup başarıyla ayrıldı.
   - Tahmin edilen kümeler ile gerçek sınıflar karşılaştırıldı.

## 📊 Görsellerin Anlamı

| Görsel | Açıklama |
|--------|----------|
| `species_distribution.png` | Hedef sınıfların dağılımı |
| `sepal_length_boxplot.png` | Sepal boyutundaki varyans ve aykırılık |
| `petal_length_histogram.png` | Petal uzunluklarının yoğunluk analizi |
| `pairplot_species.png` | Değişkenler arası ilişkiler, sınıf bazında renkli ayrım |
| `scatter_matrix.png` | Çok değişkenli ilişkilerin tüm kombinasyonları |
| `correlation_heatmap.png` | Özellikler arası korelasyon matrisi |
| `kmeans_clustering.png` | 3 küme üzerinde yapılan görsel segmentasyon |

## 📈 Sonuçlar

- En yüksek doğruluk oranı: **%98.6** (Random Forest ve XGBoost)
- Iris veri seti küçük ama ayrılabilirliği yüksek bir yapıya sahip olduğu için çoğu model başarılı sonuç verdi.
- Görselleştirmeler sınıfların yapay zeka ile rahatlıkla ayrılabileceğini kanıtladı.

## 🚀 Nasıl Çalıştırılır?

1. Ortamı oluştur:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Windows için: venv\Scripts\activate
   pip install -r requirements.txt
   ```

2. Notebook’u çalıştır:
   ```bash
   jupyter notebook notebook/saksuka_ırıs.ipynb
   ```

3. Tüm hücreleri sırayla çalıştır. Görseller `images/` klasörüne otomatik kaydedilir.

## ✅ Proje Durumu

Bu proje başarıyla tamamlandı. Kullanılan yöntemler Iris veri seti üzerinde yüksek performans gösterdi. Görsel analizler sınıfların ayırt edilebilirliğini kanıtladı. Modelleme ve kümeleme birlikte ele alınarak hem gözetimli hem gözetimsiz öğrenme uygulanmıştır.

---

Bu proje, makine öğrenmesi ve veri görselleştirme tekniklerini bir araya getiren güçlü bir başlangıç örneğidir. Veri bilimi yolculuğunda sağlam bir temel oluşturmak isteyenler için referans niteliğindedir.
