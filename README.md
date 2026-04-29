# AcademiQ_Data_Science
# Academiq Data Science 01 

PROJECT OVERVIEW, DATASET AND PIPELINE ARCHITECTURE

This project involves the initial data loading, cleaning, and preliminary exploration of a dataset titled 'github_top_repositories.csv'. The main objective has been to prepare the data for further analysis by:

Loading the Dataset: The github_top_repositories.csv file was loaded into a pandas DataFrame named dt.

Initial Data Inspection: Basic checks were performed to understand the dataset's structure, including viewing the first and last rows, checking its dimensions (number of rows and columns), and listing all column names.

Data Type and Missing Value Analysis: The dt.info() method was used to inspect data types and non-null counts for each column. A detailed analysis of missing values was conducted, showing both the count and the ratio of missing entries per column.

Column Standardization: Column names were cleaned and standardized by converting them to lowercase, replacing spaces and hyphens with underscores, and removing leading/trailing whitespace.

Data Cleaning (String Columns): All object (string) type columns were processed to remove any leading or trailing whitespace.
Handling Critical Missing Values: Rows with missing values in 'repository_name' or 'stars_count' columns were identified and removed, as these are considered critical for the dataset's integrity.

Numeric Type Conversion: Several key numeric columns ('stars_count', 'forks_count', 'watchers_count', 'open_issues_count') were explicitly converted to numeric data types, with a mechanism to handle any non-numeric entries by coercing them to NaN (Not a Number).
These steps ensure that the dataset is clean, consistently formatted, and ready for more in-depth exploratory data analysis or machine learning tasks.


#Academic Data Science 02 EDA 

Veri Yükleme ve Kütüphane Kurulumu: Analiz için gerekli olan pandas, numpy, matplotlib.pyplot, seaborn ve scipy.stats kütüphaneleri içe aktarıldı. Ardından, ecommerce_synthetic.csv adlı veri seti bir Pandas DataFrame'e yüklendi ve ilk 5 satırı (df.head()) görüntülenerek veriye hızlı bir bakış atıldı.

Sayısal Değişkenlerin İstatistiksel Analizi: churn sütunu hariç tüm sayısal sütunlar seçildi. Bu sütunlar için ortalama, medyan, ortalama/medyan oranı ve çarpıklık (skewness) değerlerini içeren karşilaştirma adında bir DataFrame oluşturuldu. Bu analiz, veri dağılımlarının dengesi ve çarpıklığı hakkında önemli bilgiler sağladı:

musteri_yasi ve siparis_sayisi sütunları ortalama/medyan oranları 1'e yakın ve çarpıklık değerleri 0'a yakın olduğu için daha dengeli ve simetrik bir dağılıma sahip görünüyor.
aylik_gelir, toplam_harcama ve ortalama_sepet sütunları ise ortalama/medyan oranlarının 1'den büyük olması ve yüksek çarpıklık değerleri nedeniyle sağa çarpık bir dağılıma sahip. Bu durum, bu sütunlarda yüksek değerli aykırı gözlemlerin (outlier) varlığını düşündürmektedir.
Eksik Değer Analizi: Veri setindeki eksik değerlerin yüzdesi hesaplandı ve eksik değer içeren sütunlar azalan sırada listelendi. Tespit edilen eksik değerler:

siparis_sayisi: %19.22
toplam_harcama: %8.74
musteri_yasi: %5.00
Ayrıca, ilk 100 satır için eksiklik paternini gösteren bir ısı haritası (heatmap) çizilerek eksikliklerin görselleştirilmesi sağlandı. Kırmızı renkler eksik değerleri temsil etmektedir.

Eksik Veri Mekanizmalarının Sınıflandırılması: siniflandir adında özel bir fonksiyon tanımlandı. Bu fonksiyon, bir sütundaki eksiklik mekanizmasının MCAR (Missing Completely At Random), MAR (Missing At Random) veya MNAR (Missing Not At Random) olup olmadığını belirlemektedir. Bu fonksiyon kullanılarak aşağıdaki sonuçlara ulaşıldı:

musteri_yasi: MCAR (rastgele eksik). Müşteri yaşı eksiklikleri tamamen rastgele görünüyor.
toplam_harcama: MAR ('aylik_gelir' ile ilişkili, p=0.0000). Toplam harcamadaki eksikliklerin aylık gelirle ilişkili olduğu, yani aylık gelirdeki belirli değerlerin toplam harcamanın eksik olma olasılığını etkilediği belirlendi.
siparis_sayisi: MCAR (rastgele eksik). Sipariş sayısı eksiklikleri de tamamen rastgele olarak sınıflandırıldı.
Bu adımlar, veri setinin genel yapısını anlamak, sayısal değişkenlerin dağılım özelliklerini keşfetmek ve eksik verilerin doğasını belirlemek için atılan temel adımlardır. Özellikle eksik veri mekanizmalarının anlaşılması, veri temizleme ve doldurma stratejileri için kritik öneme sahiptir.
