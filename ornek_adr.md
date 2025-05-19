# ADR-001: Loglama kütüphanesine karar verilmesi

- Durum: Kabul Edildi
- Tarih: 2025-05-19

## Bağlam

Projede kapsamlı bir loglama altyapısına ihtiyaç duyulmaktadır. Bu loglar:
- Geliştirme sırasında hata ayıklamayı kolaylaştırmalı,
- Gömülü sistemlerde düşük gecikme ve hafiflik sunmalı,
- Gerçek zamanlı senaryolarda bloklamaya yol açmamalı,
- Kolay yapılandırılabilir ve gerektiğinde dosya/log sunucusuna yönlendirilebilir olmalıdır.

Ek olarak, mevcut sistemde `CMake` kullanılmakta ve harici bağımlılıkların kolayca entegre edilmesi önem arz etmektedir.

## Karar

Logger kütüphanesi olarak [spdlog](https://github.com/gabime/spdlog) kullanılması kararlaştırılmıştır.

## Gerekçeler

- **Performans:** `spdlog`, sıfır allokasyon ve asenkron loglama gibi özelliklerle yüksek performans sunar.
- **Bağımsızlık:** STL harici bir bağımlılığı yoktur, sistemle kolay entegre olur.
- **Kolay kullanım:** `fmt` ile uyumlu API sayesinde kullanıcı dostudur.
- **Dosya/Döngüsel Loglama:** Günlük döndürme (rotating log) ve günlük büyüklüğüne göre sınırlandırma gibi özellikler yerleşiktir.
- **Topluluk ve destek:** Yaygın kullanıma sahiptir, aktif geliştirme devam etmektedir.
- **CMake ile kolay entegrasyon:** `FetchContent` ve `add_subdirectory` ile hızlı entegre edilir.

## Alternatifler

- **Boost.Log**
  - Artılar: Gelişmiş özellikler ve Boost ekosistemine tam uyumluluk.
  - Eksiler: Kurulum ve yapılandırma karmaşık, bağımlılık boyutu yüksek.

- **log4cpp**
  - Artılar: Olgun bir proje.
  - Eksiler: Bakımı yavaşlamış, modern C++ standartlarını yeterince desteklemiyor.

- **DIY (kendi logger sistemimizi yazmak)**
  - Artılar: Tam kontrol sağlar.
  - Eksiler: Zaman kaybı, test yükü ve hataya açıklık yaratır.

## Sonuçlar

- Projeye `spdlog` kütüphanesi `FetchContent` üzerinden entegre edilecek.
- Varsayılan olarak hem konsola hem dosyaya loglama yapan bir yapı kurulacak.
- Gömülü hedeflerde dosya loglama devre dışı bırakılabilir olacak.
- Geliştirici rehberine `spdlog` kullanım örnekleri ve stil kuralları eklenecek.
