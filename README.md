# Diyabet Hastalığı Durumunu Tahmin Etme Projesi

Bu proje, diyabet hastalığı durumunu tahmin etmek için kullanılan makine öğrenmesi algoritmalarını içermektedir. Veri seti, çeşitli biyometrik ölçümler ve hastalık durumu (HastalikDurumu) bilgilerini içermektedir.

## Veri Seti Hakkında

Veri seti, çeşitli biyometrik ölçümler ve hastalık durumu (HastalikDurumu) bilgilerinden oluşmaktadır. Toplam 537 örnek (instances) ve 9 öznitelik (attributes) içerir. Bu öznitelikler şunlardır:
- **Pregnancies**: Gebelik sayısı (numeric)
- **Glucose**: Plazma glikoz konsantrasyonu (numeric)
- **BloodPressure**: Diastolik kan basıncı (mm Hg) (numeric)
- **SkinThickness**: Triceps deri kalınlığı (mm) (numeric)
- **Insulin**: 2 saatlik serum insülin (mu U/ml) (numeric)
- **BMI**: Vücut kitle indeksi (weight in kg/(height in m)^2) (numeric)
- **DiabetesPedigreeFunction**: Soy geçmişi fonksiyonu (numeric)
- **Age**: Yaş (years) (numeric)
- **HastalikDurumu**: Diyabet hastalığı durumu (0: Hasta değil, 1: Hasta) (nominal)

## Veri Setini Ayırma Yöntemi

Veri seti, %70 eğitim ve %30 test veri seti olarak ayrılmıştır. Bu ayırma işlemi rastgele bir şekilde yapılmıştır. Bunun nedeni, rastgele ayırmanın veri setindeki örneklerin homojen bir şekilde eğitim ve test setlerine dağıtılmasını sağlamasıdır. Bu sayede, modelin her iki set için de genelleme yapabilme yeteneği artırılmış olur.

## Kullanılan Algoritmalar

### J48 (Decision Tree)
J48, C4.5 algoritmasının bir uygulamasıdır ve karar ağaçları oluşturmak için kullanılır. Verileri öznitelik değerlerine göre dallandırır ve yapraklar sınıf etiketlerini temsil eder. Karar ağacı, sınıflandırma kararlarını görselleştirmek için oldukça kullanışlıdır.

### SMO (Support Vector Machine)
SMO, Support Vector Machine (SVM) algoritmasının bir uygulamasıdır. Doğrusal veya doğrusal olmayan bir ayırıcı hiper düzlem oluşturarak veri noktalarını sınıflandırır. SMO, ikili sınıflandırma problemlerinde kullanılır ve veri setinde sınıflar arasındaki en iyi ayrımı bulmaya çalışır.

## Elde Edilen Sonuçlar

### J48 (Decision Tree)
- **Doğru Sınıflandırılan Örnekler**: 167 (72.29%)
- **Yanlış Sınıflandırılan Örnekler**: 64 (27.71%)
- **Kappa İstatistiği**: 0.3524
- **Ortalama Mutlak Hata (MAE)**: 0.3295
- **Kök Ortalama Kare Hata (RMSE)**: 0.4647
- **Göreceli Mutlak Hata (RAE)**: 72.32%
- **Kök Göreceli Kare Hata (RRSE)**: 97.09%

### SMO (Support Vector Machine)
- **Doğru Sınıflandırılan Örnekler**: 169 (73.16%)
- **Yanlış Sınıflandırılan Örnekler**: 62 (26.84%)
- **Kappa İstatistiği**: 0.3652
- **Ortalama Mutlak Hata (MAE)**: 0.2684
- **Kök Ortalama Kare Hata (RMSE)**: 0.5181
- **Göreceli Mutlak Hata (RAE)**: 58.91%
- **Kök Göreceli Kare Hata (RRSE)**: 108.25%

## Yorumlar ve Karşılaştırmalar

- **Doğruluk Oranı**: SMO algoritması, J48 algoritmasına göre biraz daha yüksek doğruluk oranı (%73.16 vs. %72.29) göstermektedir.
- **Kappa İstatistiği**: SMO algoritmasının Kappa değeri, J48'e göre daha yüksek (0.3652 vs. 0.3524), bu da modelin rastgele sınıflandırmaya kıyasla daha iyi performans gösterdiğini belirtir.
- **Hatalar**: SMO algoritması daha düşük bir ortalama mutlak hata (MAE) ve göreceli mutlak hata (RAE) değeri göstermektedir, bu da tahminlerin gerçek değerlere daha yakın olduğunu gösterir.
- **Sınıflar Arası Performans**: Her iki algoritma da sınıf 0 için daha iyi performans gösterirken, sınıf 1 için performansları daha düşüktür. Bu dengesizlik, veri setinizde sınıf 0'ın daha fazla temsil edilmesinden kaynaklanıyor olabilir.
- **Model Seçimi**: Genel olarak, SMO algoritması biraz daha yüksek doğruluk ve daha düşük hata oranları göstermektedir. Ancak, J48 algoritması karar ağaçlarının görselleştirilebilirliği sayesinde daha anlaşılır olabilir.

## Nasıl Çalıştırılır

1. Weka'yı indirin ve yükleyin: [Weka İndir](https://www.cs.waikato.ac.nz/ml/weka/downloading.html)
2. Pyton kodunu çalıştırarak mevcut veri setini ayrıştırabilirsiniz. 
   (gerekli sanal oratamı oluşturmak için: python -m venv venv & pip install -r requirements.txt)
3. Weka'yı başlatın ve "Explorer" moduna geçin.
4. "Preprocess" sekmesinde `.arff` uzantılı `traindatasetinizi` dosyasını ykleyin.
5. "Classify" sekmesine geçin ve algoritma olarak J48 veya SMO'yu seçin.
6. "Test options" bölümünde "Supplied test set" seçeneğini işaretleyin ve `.arff` uzantılı `testdatasetinizi` dosyasını yükleyin.
7. "Start" butonuna tıklayarak modeli eğitin ve test edin.


