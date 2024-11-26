![PostgreSQL Error](https://github.com/user-attachments/assets/d2d74b46-6079-4e7f-bf78-2b5e08d1e501)

# Windows 11 PostgreSQL 17: "The Database Cluster Initialization Failed" Hatası Çözümü

Bu rehber, PostgreSQL 17'yi kurarken karşılaşılan "The database cluster initialization failed" hatasını çözmenize yardımcı olacaktır. Bu hata, PostgreSQL veritabanı kümesinin başlatılmaya çalışıldığı ancak başarısız olduğu durumlarda görülür. Aşağıdaki adımları takip ederek bu hatayı çözebilirsiniz. Adım 4 en kesin çözümdür.

## Adım 1: Yönetici Olarak Komut İstemcisini (CMD) Açın

Bu hatayı çözebilmek için komutları yönetici olarak çalıştırmanız gerekecektir. Yönetici olarak Komut İstemcisi'ni açmak için şu adımları izleyin:

1. **Başlat Menüsüne** gidin.
2. "cmd" yazın ve çıkan **Komut İstemcisi** uygulamasına sağ tıklayın.
3. **Yönetici olarak çalıştır** seçeneğine tıklayın.
4. Ardından, PostgreSQL'in yüklü olduğu dizine gitmek için aşağıdaki komutu kullanın:

```bash
cd "C:\Program Files\PostgreSQL\17\bin"
```

## Adım 2: Veri Kümesini Yeniden Başlatmayı Deneyin

PostgreSQL'in veri kümesini yeniden başlatmayı deneyin. Bunun için aşağıdaki komutu kullanabilirsiniz:

```bash
initdb -D "C:\Program Files\PostgreSQL\17\data" -U postgres --locale="tr_TR.utf8"
```

Bu komut, PostgreSQL veritabanı kümesini belirtilen dizine oluşturur. Eğer bu komut başarısız olursa, hata mesajını dikkatlice inceleyin. Genellikle eksik izinler veya dosya yolu hataları nedeniyle işlem başarısız olabilir.

## Adım 3: PostgreSQL Hizmetini Kaydedin ve Başlatın

Eğer yukarıdaki adımlar sorununuzu çözmediyse, PostgreSQL hizmetini manuel olarak kaydedin ve başlatın. Aşağıdaki komutları kullanarak bunu yapabilirsiniz:

### Hizmeti Kaydetme

```bash
pg_ctl.exe register -N "PostgreSQL" -U "NT AUTHORITY\NetworkService" -D "C:\Program Files\PostgreSQL\17\data" -w
```

### Hizmeti Başlatma

```bash
pg_ctl start -D "C:\Program Files\PostgreSQL\17\data"
```

Bu komutlar, PostgreSQL hizmetini Windows hizmeti olarak kaydeder ve başlatır.

## Adım 4: PostgreSQL'i Yeniden Kurun

Eğer yukarıdaki adımların hiçbiri sorunu çözmediyse, kesin çözüm olarak PostgreSQL'i kaldırıp yeniden kuruyoruz. Dikkat etmemiz gereken tek şey, kurulum sırasında Locale seçimini doğru yapmaktır. Eğer bilgisayarınızın bölgesi Türkiye ise, kurulum sırasında Default Locale olarak English (United States) seçip kurulumu tamamlayın.
