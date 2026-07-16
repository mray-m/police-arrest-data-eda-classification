# Police Arrest Data — EDA & Classification

ABD'de bir eyalet tarafından yayınlanan Police Transparency – Arrests veri seti üzerinde modelleme çalışmaları gerçekleştirilmiştir. Proje kapsamında veri analizi, veri ön işleme, özellik mühendisliği, model geliştirme ve performans değerlendirme adımları uygulanmıştır.

## 📊 Veri Seti

- **Kaynak:** [data.gov – Police Transparency: Arrests (All Data, main table denormalized)](https://catalog.data.gov/dataset/police-transparency-arrests-all-data-main-table-denormalized)
- Tutuklama kayıtlarını; tutuklunun ırk/etnisite, yaş aralığı, cinsiyet bilgilerini, suç ciddiyetini (felony/misdemeanor), tutuklama tipini, tarih-saat bilgisini ve coğrafi konum verilerini içerir.

## 📁 İçerik

| Dosya | Açıklama |
|---|---|
| `analiz.ipynb` | Keşifsel veri analizi (EDA): eksik değer analizi, tekrarlayan satır kontrolü, ırk/etnisiteye göre suç ciddiyeti dağılımı (crosstab), pair plot görselleştirmeleri |
| `modelleme.ipynb` | Veri ön işleme, feature engineering ve sınıflandırma modellemesi |
| `dataset_linki.txt` | Ham veri setinin data.gov bağlantısı |

## 🔍 Keşifsel Veri Analizi (`analiz.ipynb`)

- Eksik değerlerin sütun bazında sayı ve yüzde olarak incelenmesi
- Tekrarlayan satırların kontrolü
- Özellikler ile hedef değişken arasında karşılıklı bilgi (mutual information) skorları
- Irk/etnisiteye göre suç ciddiyeti (Felony / Misdemeanor / Unknown) yüzde dağılımı
- Sayısal değişkenler için pair plot görselleştirmesi

## 🛠️ Modelleme (`modelleme.ipynb`)

**Ön İşleme Adımları:**
- Tekilleştirme ve gereksiz sütunların (ID, koordinat, memur bilgisi vb.) çıkarılması
- IQR yöntemiyle aykırı değer tespiti ve temizliği
- Sayısal değişkenlerde mod ile, kategorik değişkenlerde dağılım koruyarak imputasyon
- Tutuklama tarihinden yıl / ay / haftanın günü / günün zaman dilimi gibi yeni özelliklerin türetilmesi (feature engineering)
- One-Hot Encoding ve `StandardScaler` ile ölçeklendirme
- ANOVA F-testi (`SelectKBest`) ile en anlamlı özelliklerin seçimi

**Hedef Değişken:**
- `is_onview_arrest`: Tutuklamanın olay yerinde (on-view) yapılıp yapılmadığını gösteren ikili (binary) değişken

**Kullanılan Modeller:**
- Dummy Classifier (baseline)
- Naive Bayes (`GaussianNB`)
- Random Forest (`RandomizedSearchCV` ile hiperparametre optimizasyonu, sınıf dengesizliği için `class_weight='balanced'`)

**Değerlendirme Metrikleri:** Accuracy, Precision, Recall, F1-score, ROC-AUC

## 🧰 Kullanılan Teknolojiler
 
- **Python**
- **Jupyter Notebook**
- **Pandas** & **NumPy** — veri işleme ve analiz
- **Matplotlib** & **Seaborn** — veri görselleştirme
- **Scikit-learn** — özellik seçimi (`SelectKBest`), ölçeklendirme (`StandardScaler`), model geliştirme (`GaussianNB`, `RandomForestClassifier`, `DummyClassifier`) ve hiperparametre optimizasyonu (`RandomizedSearchCV`)

## 👩‍💻 Geliştirici

**Miray Merve Durmuş** — [@mray-m](https://github.com/mray-m)


