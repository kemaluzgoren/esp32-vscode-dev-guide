# idf.py Komut Referansı

Bu belge, ESP-IDF projelerinde kullanılan `idf.py` komut satırı aracının tüm önemli komutlarını ve parametrelerini açıklar. `idf.py`, ESP32 serisi cihazlar için yapı, konfigürasyon, yükleme ve hata ayıklama işlemlerinde kullanılır.

---

## 🧭 Genel Kullanım

```bash
idf.py [OPTIONS] COMMAND1 [ARGS]... [COMMAND2 [ARGS]...]
```

---

## ⚙️ Genel Seçenekler (`[OPTIONS]`)

| Seçenek | Açıklama |
|--------|----------|
| `--version` | Yüklü ESP-IDF sürümünü gösterir. |
| `--list-targets` | Desteklenen tüm ESP32 çip modellerini listeler. |
| `-C`, `--project-dir PATH` | Proje dizinini belirtir. Varsayılan: mevcut dizin. |
| `-B`, `--build-dir PATH` | Build çıktılarının yer alacağı dizini belirtir. |
| `-v`, `--verbose` | Daha ayrıntılı log çıktısı verir. |
| `-p`, `--port` | ESP32'nin bağlı olduğu seri portu belirtir (örn: COM3, /dev/ttyUSB0). |
| `-b`, `--baud` | Flash ve monitor baud hızını belirtir. |
| `-G`, `--generator [Ninja]` | Kullanılacak CMake generator’ü. Genellikle `Ninja` tercih edilir. |
| `--ccache / --no-ccache` | `ccache` ile daha hızlı tekrar derleme sağlar. |
| `--preview` | Geliştirme aşamasındaki IDF özelliklerini aktif eder. |
| `--no-hints` | Hata mesajlarında önerilen çözümleri kapatır. |
| `-D`, `--define-cache-entry TEXT` | CMake cache girişi oluşturur. |
| `--help` | Yardım sayfasını gösterir. |

---

## 🛠️ Komutlar (`COMMAND`)

### 🔧 Derleme ve Flash

| Komut | Açıklama |
|--------|----------|
| `set-target` | Hedef çipi seçer (`esp32`, `esp32c6` gibi). |
| `build` / `all` | Projeyi derler. |
| `app` | Sadece uygulama kısmını derler. |
| `bootloader` | Sadece bootloader’ı derler. |
| `partition-table` | Sadece partition table’ı derler. |
| `flash` | Tüm bileşenleri karta yükler. |
| `app-flash` | Sadece uygulamayı karta yükler. |
| `bootloader-flash` | Sadece bootloader’ı yükler. |
| `partition-table-flash` | Sadece partition table’ı yükler. |
| `encrypted-flash` | Şifrelenmiş imajları yükler. |
| `erase-flash` | Flash belleği tamamen siler. |
| `reconfigure` | CMake yapılandırmasını yeniler. |
| `clean` | Derleme çıktısını temizler. |
| `fullclean` | Tüm build ve konfigürasyon dosyalarını siler. |

### 🔍 İzleme ve Debug

| Komut | Açıklama |
|--------|----------|
| `monitor` | Seri porttan logları takip eder. |
| `flash monitor` | Yükleme sonrası otomatik log takibi başlatır. |
| `gdb` | GDB debug oturumu başlatır. |
| `gdbgui` | GDB'yi web tabanlı GUI ile başlatır. |
| `gdbtui` | GDB'nin terminal tabanlı TUI modunu başlatır. |
| `openocd` | OpenOCD sunucusunu başlatır. |

### ⚙️ Konfigürasyon ve Bilgi

| Komut | Açıklama |
|--------|----------|
| `menuconfig` | Konfigürasyon arayüzü (konsol menüsü). |
| `size` | Uygulama RAM ve flash kullanımını gösterir. |
| `size-components` | Bileşen bazlı bellek kullanımını gösterir. |
| `size-files` | Dosya bazlı bellek kullanımını gösterir. |
| `save-defconfig` | `sdkconfig.defaults` dosyası üretir. |

### 🔐 Güvenlik ve eFuse

| Komut | Açıklama |
|--------|----------|
| `efuse-dump` | Tüm eFuse değerlerini gösterir. |
| `efuse-summary` | eFuse özet bilgilerini verir. |
| `efuse-burn` | eFuse yakma işlemi yapar. |
| `efuse-read-protect` | Belirtilen alanı yazmaya karşı korur. |
| `secure-*` | Secure Boot, flash şifreleme ve imzalama işlemleri. |

### 🧪 Diğer / Gelişmiş

| Komut | Açıklama |
|--------|----------|
| `create-project` | Yeni bir proje başlatır. |
| `create-component` | Yeni bir bileşen (component) oluşturur. |
| `docs` | ESP-IDF dokümantasyonunu tarayıcıda açar. |
| `clang-check`, `clang-html-report` | Kod analizi araçları. |
| `qemu` | Sanal cihaz üzerinde çalıştırma (deneysel). |

---

## ✅ Örnek Kullanımlar
```bash
idf.py set-target esp32
idf.py menuconfig
idf.py build
idf.py -p COM3 flash monitor
```

---

Bu doküman, `idf.py` komutlarını hem yeni başlayanlar hem de ileri seviye kullanıcılar için referans niteliğinde sunar. Geliştirme sürecinde sık kullanılan komutları ve anlamlarını kolayca bulmak için kullanılabilir.
