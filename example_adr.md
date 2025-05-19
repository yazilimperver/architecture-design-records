# ADR-001: Veritabanı olarak PostgreSQL seçimi

**Durum:** Kabul Edildi  
**Tarih:** 2025-05-19

## Bağlam
Yeni mikroservis tabanlı sistemimizde ilişkisel veri saklamamız gerekiyor. Performans, açık kaynak olması, güçlü topluluk desteği ve ACID garantileri bizim için önemli.

## Karar
Veritabanı sistemi olarak PostgreSQL kullanılmasına karar verilmiştir.

## Gerekçeler
- Açık kaynak ve lisans maliyeti yok
- SQL standardına yüksek uyumluluk
- JSONB desteği sayesinde yarı-yapısal veriyle de çalışabiliyor
- Topluluk desteği ve araç çeşitliliği güçlü
- Daha önce ekip içinde PostgreSQL deneyimi mevcut

## Alternatifler
- **MySQL:** JSON desteği daha zayıf, topluluk tercihimiz PostgreSQL yönünde
- **MongoDB:** NoSQL çözüm, ancak ilişkisel model için uygun değil
- **MS SQL Server:** Lisans maliyeti nedeniyle elendi

Burada her bir seçenek tablo şeklinde verilip, karşılaştırma yapılabilir.

## Sonuçlar
- PostgreSQL kurulumu yapılacak
- ORM olarak Sequelize tercih edilecek
- Yapılandırmalar .env üzerinden yönetilecek
