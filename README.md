# AdaBoost ile Diyabet Tahmini ve Model Karşılaştırması

Bu depo, tıbbi teşhis verilerine dayanarak diyabet başlangıcını tahmin etmeyi amaçlayan bir makine öğrenmesi projesini içermektedir. Projenin temel odak noktası, `GridSearchCV` kullanılarak bir **AdaBoost Sınıflandırıcısının** optimize edilmesi ve performansının diğer geleneksel makine öğrenmesi modelleriyle karşılaştırılmasıdır.

##  Veri Seti
Bu projede kullanılan veri seti, tıbbi bağımsız değişkenleri ve bir hedef değişkeni (`Outcome`) içermektedir.
* **Bağımsız Değişkenler:** Hamilelik Sayısı (Pregnancies), Glikoz, Kan Basıncı (BloodPressure), Cilt Kalınlığı (SkinThickness), İnsülin, Vücut Kitle İndeksi (BMI), Diyabet Soyağacı İşlevi (DiabetesPedigreeFunction), Yaş.
* **Hedef Değişken:** Sonuç (0 = Sağlıklı, 1 = Diyabet Hastası)

##  İş Akışı ve Metodoloji

1.  **EDA:**
    * `seaborn` ve `matplotlib` kullanılarak veri dağılımları görselleştirildi.
    * Belirli özellikler (örneğin Diyabet Soyağacı İşlevi) ile hedef değişken arasındaki ilişki analiz edildi.
2.  **Veri Ön İşleme:**
    * Kritik biyolojik özelliklerdeki (Glikoz, Kan Basıncı, Cilt Kalınlığı, İnsülin, BMI) geçersiz `0` değerleri tespit edildi ve veri setinden filtrelendi.
    * Veri seti eğitim (%80) ve test (%20) olmak üzere ikiye ayrıldı.
    * Optimum model performansı için özellikler `StandardScaler` kullanılarak standartlaştırıldı.
3.  **Model Eğitimi ve Hiperparametre Optimizasyonu:**
    * Temel model olarak `AdaBoostClassifier` uygulandı.
    * Optimum hiperparametreleri (`n_estimators`, `learning_rate`) bulmak için `GridSearchCV` kullanıldı.
4.  **Karşılaştırmalı Analiz:**
    * Optimize edilen AdaBoost modeli; **Lojistik Regresyon**, **Destek Vektör Sınıflandırıcısı (SVC)** ve **Naive Bayes** modelleriyle karşılaştırılarak değerlendirildi.

##  Bulgular
Modeller; Accuracy, Precision, Recall ve F1-Skoru metriklerine göre değerlendirilmiştir. 

| Model | Doğruluk Skoru (Accuracy) |
| :--- | :--- |
| **AdaBoost (Optimize Edilmiş)** | **%82.0** |
| Naive Bayes | %79.7 |
| Lojistik Regresyon | %77.2 |
| Destek Vektör Sınıflandırıcısı (SVC) | %77.2 |

*Sonuçlar, hiperparametre optimizasyonu yapılmış AdaBoost algoritmasının diyabet tahmininde diğer temel makine öğrenmesi modellerinden daha yüksek performans gösterdiğini ortaya koymaktadır.*

##  Kullanılan Teknolojiler ve Kütüphaneler
* **Python 3.x**
* **Pandas & NumPy** (Veri İşleme)
* **Scikit-Learn** (Makine Öğrenmesi, Ön İşleme, Değerlendirme)
* **Seaborn & Matplotlib** (Veri Görselleştirme)
