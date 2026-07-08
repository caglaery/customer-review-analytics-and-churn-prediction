# Müşteri Yorum Analizi ve Churn Tahmin Sistemi

## Proje Hakkında

Bu projede mobil bankacılık uygulamalarına ait müşteri yorumları kullanılarak doğal dil işleme (NLP), özellik mühendisliği (Feature Engineering) ve makine öğrenmesi yöntemleri ile müşteri davranışları analiz edilmiştir.

Projenin amacı yalnızca yorumların olumlu veya olumsuz olduğunu belirlemek değil, müşteri davranışlarını analiz ederek müşteri kaybı (churn) riski taşıyan kullanıcıları erken aşamada tespit etmektir.

Bu kapsamda iki farklı makine öğrenmesi problemi ele alınmıştır.

### 3 Segmentli Müşteri Sınıflandırması

* Sadık
* Şikayetçi
* Sessiz Kayıp

### 2 Segmentli Churn Tahmini

* Sadık
* Riskli

---

# İş Problemi

Mobil bankacılık uygulamalarında yalnızca yıldız puanlarına bakılarak müşteri memnuniyetini ölçmek çoğu zaman yeterli değildir.

Örneğin;

* 5 yıldız verip olumsuz yorum yazan müşteriler,
* Düşük puan vermesine rağmen uygulamayı kullanmaya devam eden müşteriler,
* Yorumlarında bankayı bırakacağını açıkça belirten kullanıcılar,

klasik duygu analizi yöntemleriyle doğru şekilde tespit edilemeyebilir.

Bu proje, müşteri yorumlarından davranışsal sinyaller çıkararak olası müşteri kayıplarını önceden belirlemeyi amaçlamaktadır.

---

# Veri Seti

Projede Türkiye'deki mobil bankacılık uygulamalarına ait müşteri yorumları kullanılmıştır.

Kullanılan temel değişkenler:

* Banka
* Yorum
* Yıldız Puanı
* Uygulama Versiyonu
* Tarih

---

# Özellik Mühendisliği (Feature Engineering)

Projede ham verilerden çeşitli davranışsal değişkenler üretilmiştir.

## NLP Tabanlı Özellikler

* Duygu Skoru
* Duygu Etiketi
* Delta Skoru
* Delta Sinyali

## Davranışsal Özellikler

* Sürtünme Skoru
* Churn Niyeti Skoru
* Yorum Uzunluğu
* Emoji Sayısı

---

# Müşteri Segmentasyonu

Müşteriler kural tabanlı olarak üç gruba ayrılmıştır.

### Sadık

Yorumları ve yıldız puanı genel olarak olumlu olan müşteriler.

### Şikayetçi

Memnuniyetsizliğini açık şekilde ifade eden müşteriler.

### Sessiz Kayıp

Yıldız puanı yüksek görünmesine rağmen yorumlarında memnuniyetsizlik sinyalleri bulunan ve gelecekte bankayı terk etme riski taşıyan müşteriler.

---

# Kullanılan Makine Öğrenmesi Modelleri

Projede iki farklı sınıflandırma problemi çözülmüştür.

## Üç Segmentli Sınıflandırma

* Logistic Regression
* Random Forest

## İki Segmentli Churn Tahmini

* Logistic Regression
* Random Forest

---

# Model Değerlendirme

Modeller aşağıdaki metriklerle değerlendirilmiştir.

* Accuracy
* Precision
* Recall
* F1 Score
* 5 Katlı Cross Validation
* Confusion Matrix
* ROC Curve (2 Segment)
* Feature Importance

---

# Model Sonuçları

| Problem   | Model               |  Accuracy | Precision |    Recall |  F1 Score |
| --------- | ------------------- | --------: | --------: | --------: | --------: |
| 3 Segment | Random Forest       |     0.668 |     0.741 |     0.668 |     0.699 |
| 3 Segment | Logistic Regression | **0.743** |     0.674 | **0.743** | **0.703** |
| 2 Segment | Random Forest       |     0.781 |     0.683 | **0.800** | **0.737** |
| 2 Segment | Logistic Regression | **0.791** | **0.751** |     0.683 |     0.715 |

---

# Sonuçların Yorumu

## 3 Segmentli Problem

Üç segmentli sınıflandırma problemi, **Sessiz Kayıp** sınıfının veri setinin yalnızca yaklaşık **%8,6'sını** oluşturması nedeniyle daha zordur. Bu durum sınıflar arasında dengesizliğe neden olmaktadır.

Buna rağmen Logistic Regression modeli %74,3 doğruluk oranı ile en yüksek Accuracy değerine ulaşmıştır. Random Forest modeli ise benzer F1 skoruna ulaşarak rekabetçi bir performans sergilemiştir.

## 2 Segmentli Problem

İkili sınıflandırmada iki model birbirine yakın performans göstermiştir.

* Logistic Regression modeli en yüksek doğruluk oranına (%79,1) ulaşmıştır.
* Random Forest modeli ise en yüksek Recall (%80) ve F1 Score (0.737) değerlerini elde etmiştir.

Müşteri kaybı tahmini gibi risk odaklı problemlerde yüksek Recall ve F1 Score önemli olduğundan, operasyonel kullanım açısından Random Forest modeli güçlü bir alternatif sunmaktadır.

---

# İş Çıkarımları

Bu proje sonucunda aşağıdaki bulgular elde edilmiştir.

* Sürtünme skoru ve churn niyeti skoru müşteri kaybını tahmin etmede en etkili davranışsal değişkenlerdir.
* Emoji sayısı, soru işareti sayısına kıyasla daha güçlü bir davranışsal sinyal sağlamıştır.
* Sessiz Kayıp segmenti toplam müşterilerin yaklaşık %8,6'sını oluşturmaktadır ve model açısından sınıflandırılması en zor gruptur.
* Müşteri yorumlarından elde edilen davranışsal sinyaller, yalnızca yıldız puanına dayalı analizlere göre daha fazla içgörü sağlamaktadır.

---

# Kullanılan Teknolojiler

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Natural Language Processing (NLP)
* Machine Learning

---

# Proje Çıktıları

* Veri temizleme ve ön işleme
* NLP tabanlı duygu analizi
* Özellik mühendisliği
* Kural tabanlı müşteri segmentasyonu
* Churn tahmin modeli
* Feature Importance analizi
* Confusion Matrix
* ROC Curve
* Model karşılaştırmaları
* İş odaklı analizler
  <img width="532" height="504" alt="image" src="https://github.com/user-attachments/assets/554ac174-ef03-49e3-b98c-af4501af5bdf" />
  <img width="2484" height="1584" alt="image" src="https://github.com/user-attachments/assets/ae82ca5f-84b4-47ea-864c-2e70e2f00da7" />
  <img width="1784" height="495" alt="image" src="https://github.com/user-attachments/assets/ab1a8b74-3b8e-4443-ad02-9af9b3b975e1" />



