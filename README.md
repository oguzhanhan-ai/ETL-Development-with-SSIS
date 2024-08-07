# ETL-Development-with-SSIS

![etl_processes](https://github.com/user-attachments/assets/756a449b-158e-4802-af48-1a5e8cffc79e)

## 1. ETL Nedir?

ETL; **Extract**, **Transform** ve **Load** kelimelerinin baş harflerinden oluşmaktadır. ETL, kabaca verinin kaynak bir sistemden alınıp, belirli işlemlerden geçirildikten sonra hedef bir sisteme yüklenmesi işidir.

**Extract (Ayıklama):** Kaynak sistemden veriyi okumak anlamına gelir.

**Transform (Dönüştürme):** Okuduğumuz veri üzerine farklı dönüşüm işlemlerinin gerçekleştirilmesidir.

**Load (Yükleme):** Dönüştürdüğümüz ve üzerinde çeşitli hesaplamalar yapmış olduğumuz verinin hedef bir sisteme yüklenmesi anlamına gelir.

## 2. SSIS (SQL Sever Integration Services) Nedir?

**SSIS (SQL Server Integration Services)** Microsoft'un veri taşıma, dönüştürme ve yükleme işlemleri için geliştirmiş olduğu bir **ETL (veri yükleme ve senkronizasyon)** platformudur. SSIS ile farklı veri kaynakları arasında veri senkronizasyonu, veri taşıma, dönüştürme ve yükleme işlemleri gerçekleştirilebilir. 

SSIS, bu noktada her ne kadar bir ETL aracı olsa da ETL işlemleri mutlaka SSIS ile gerçekleştirilmesi gereken süreçler değildir. ETL süreçleri SQL kodlarıyla, Python diliyle vb. araçlarla da gerçekleştirilebilir.

## 3. SSIS Kurulumu Hakkında Bilinmesi Gerekenler

SSIS ile ETL işlemlerini gerçekleştirebilmek için bilgisayarımızda kurulu olması gereken 2 ana uygulama bulunmaktadır:

Bunlardan birincisi SSIS servisinin kendisidir. İkincisi ise Microsoft tarafından geliştirilen **SSDT (SQL Server Data Tools)** isimli Visual Studio eklentisidir.

SSDT aslında Microsoft tarafından geliştirilen bir **İş Zekası** paketidir. Haliyle içerisinde SSIS ile birlikte gelen şu 3 farklı servis yer almaktadır:

- **SQL Server Analysis Services (SSAS)**
- **SQL Server Reporting Services (SSRS)**
- **SQL Server Integration Services (SSIS)**

## 4. SSIS Kullanım Alanları

SSIS, şirketlerin büyük veri entegrasyonu ve veri ambarı geliştirme gibi ihtiyaçlarını karşılamak üzere geniş yelpazade çözümler sunabilir:

**a) Veri Entegrasyonu:** SSIS, farklı veri kaynakları arasındaki veri senkronizasyonunu sağlar. Örneğin, bir CRM sistemi ile finansal bir sistem arasında veri aktarımı gerçekleştirebilirsiniz.

**b) Veri Taşıma:** SSIS, farklı veri kaynaklarından gelen verilerin, veri depolama alanlarına taşınması işlemlerini gerçekleştirebilir. Örneğin, bir web sitesinden veri toplayabilir ve bunu bir veritabanına yükleyebilirsiniz.

**c) Veri Dönüştürme:** SSIS, farklı veri kaynaklarından gelen veriler üzerinde çeşitli dönüşüm işlemleri gerçekleştirerek, veriyi veri depolama alanlarına uygun hale getirebilir. Örneğin, bir kaynak verideki tarihlerin formatını değiştirebilir veya veri kümelerini birleştirebilirsiniz.

**d) Veri Yükleme:** SSIS, farklı veri kaynaklarından gelen verileri veri depolama alanlarına yükleyebilir. Örneğin, bir veritabanına veri yükleyebilir veya bir dosyaya yazabilirsiniz.

## 5. SSDT Arayüzünü Tanıyalım

**1. Yeni Bir SSIS Projesi Oluşturma:** Öncelikli olarak Visual Studio Community ortamında, yeni bir SSIS (SQL Server Integration Services) projesi oluşturmak için sırasıyla **File** ve **New** butonlarına basıyoruz ve buradan **Project** seçeneğini seçiyoruz. Daha sonrasında ise C# projelerinden farklı olarak **Business Intelligence** başlığı altında yer alan **Integration Services** seçeneğini seçerek  projemize bir isim veriyoruz.

**2. SSIS Toolbox:** Sol tarafta görülen ekran **SSIS Toolbox** olarak adlandırılmaktadır. Aslında burası bizim tüm ETL süreçlerini tasarkarken kullanacak olduğumuz tüm kompenentlerin yani (bileşenlerin) yer aldığı menü olarak özetlenebilir. Bu noktada herhangi bir bileşen ilk defa kullanılacak olduğunda üzerinde küçük bir hatırlatma yazısı görebilirsiniz.

**3. Solution Explorer:** Sağ taraftaki **Solution Explorer** penceresi ise, oluşturmuş olduğunuz projelerin klasör yapısını ve içeriğini gösterir. Bu pencere üzerinden projelerinizin dosyalarını ve alt bileşenlerini görebilir ve yönetebilirsiniz.

**4. Dizayn (Canvas) Alanı:** Orta kısımda yer alan boş alan ise, ETL süreçlerini tasarlayacağımız **dizayn (canvas)** alanıdır. Bu alan içerisine, sol taraftaki SSIS Toolbox’tan ilgili bileşenleri sürükleyip bırakarak ETL süreçlerinizi tasarlayabilirsiniz. Dizayn alanı, bileşenleri, veri akışını ve dönüşüm işlemlerini düzenler.

**5. Connection Managers:** Dizayn alanının en altında yer alan **Connection Managers** sekmesi, ETL projelerinizde kullandığınız veri bağlantı bilgilerini gösterir. Buradan mevcut veri kaynaklarına ve hedef bileşenlere ait bağlantı bilgileri ekleyebilir, düzenleyebilir veya kaldırabilirsiniz.

**6. Variables:** Connection Managers sekmesinin daha altında bulunan **Variables** sekmesi ise, proje özelinde oluşturmuş olduğumuz değişkenleri listeler. Buradan yeni değişkenler oluşturabilir, mevcut değişkenleri düzenleyebilir veya silebiliriz. Bu değişkenler, veri akışı süreçlerinde dinamik değerler taşımak ve işlevselliği artırmak için kullanılır.

## 6. Temel SSIS Bileşenleri

**1. Control Flow:** Control Flow ekranı, SSIS projelerinin genel akışını düzenler ve yönetir. Bu ekran, ETL süreçleri için gerekli olan genel işlemleri ve iş akışlarını tanımlamamıza olanak sağlar. İşte Control Flow ile ilgili bazı temel noktalar:

- **Giriş Ekranı:** Visual Studio Community ortamında yeni bir proje oluşturduğunuzda, ilk olarak Control Flow ekranı ile karşılaşılır. Bu ekran, ETL işlemlerinin genel çerçevesini oluşturur.

- **Data Flow ve Diğer Görevler:** Control Flow, ETL işlemlerinin dışında kalan iş akışlarını ve görevleri düzenler. Data Flow, bu yapının bir bileşenidir ve kontrol akışını yönetir. Control Flow ekranında, **Data Flow Task** bileşenini kullanarak Data Flow ekranına geçebilirsiniz.

- **Görevler ve Akışlar:** Control Flow içerisinde görevler, akışlar, ve diğer kontroller (örneğin, koşul kontrolleri) ekleyebilirsiniz. Bu görevler, veri akışlarını yönlendiren, döngüler oluşturan veya hata yönetimi yapan işlemleri içerebilir.

**2. Data Flow:** Data Flow, verilerin taşınmasını, dönüştürülmesini ve hedefe yazılmasını düzenleyen bir bileşendir. Control Flow içerisinde **Data Flow Task** olarak kullanılır ve Data Flow ekranında detaylı veri yönetimi işlemleri yapılır. Data Flow ekranı içerisinde veri yönetimi işlemleri için kullanabileceğiniz 3 çeşit bileşen yer almaktadır:

- **Other Sources:** Kaynak bileşenleri
- **Other Transform:** Veri üzerinde çeşitli dönüşümler ve hesaplamalar yapabileceğimiz dönüşüm bileşenlerinin yer aldığı kısımdır.
- **Other Destination**: Herhangi bir kaynaktan okuduğumuz ve üzerinde birtakım değişiklikler yaptığımız verileri hedef bir sisteme yazmamızı sağlayan bileşenlerdir.
