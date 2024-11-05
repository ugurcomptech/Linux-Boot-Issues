# GRUB Rescue Hatası ve Çözümü

## Hata Tanımı
`grub rescue>` moduna geçiş, genellikle GRUB'un doğru yapılandırılmadığı veya gerekli dosyaları bulamadığı durumlarda meydana gelir. Bu hata, sistemin başlatılmasını engeller ve kullanıcıyı komut satırına yönlendirir.

## Hatanın Nedenleri
1. **Yanlış Disk veya Bölüm Yapısı**: GRUB, işletim sisteminin bulunduğu bölümü tespit edemediğinde bu hatayı verebilir.
2. **GRUB Yapılandırma Dosyalarının Hatalı Olması**: `grub.cfg` veya diğer yapılandırma dosyaları bozulduğunda veya yanlış ayarlandığında bu sorun yaşanabilir.
3. **Disk Arızası**: Donanımsal bir sorun nedeniyle disk veya bölümlerin erişimi kısıtlanmış olabilir.
4. **Yanlış Yükleme**: GRUB'un yüklenmediği veya yanlış bir bölüme yüklendiği durumlar da hataya neden olabilir.

## Çözüm Adımları

### 1. GRUB'un Normal Modda Yüklenmesi
`grub rescue>` modunda, aşağıdaki komutları kullanarak GRUB'un normal modda yüklenmesini sağlayın:
```bash
set root=(hd0,msdos2)
set prefix=(hd0,msdos2)/boot/grub
insmod normal
normal
```

### 2. GRUB'un Yeniden Kurulması
Sistem açıldıktan sonra terminalde aşağıdaki komutları çalıştırarak GRUB'u yeniden kurun:
```bash
sudo update-grub
sudo grub-install /dev/sda
```

### 3. Yapılandırma Dosyasını Kontrol Edin
`/etc/default/grub` dosyasını açarak yapılandırma ayarlarını kontrol edin:
```bash
sudo nano /etc/default/grub
```
Bu dosyada `GRUB_DEFAULT` ve `GRUB_TIMEOUT` ayarlarını uygun şekilde düzenleyin.

### 4. Disk ve Bölüm Durumunu Kontrol Edin
Disk yapılandırmanızı kontrol etmek için şu komutu kullanın:
```bash
sudo fdisk -l
```

### 5. Sistemi Yeniden Başlatın
Yapılandırmalarınızı tamamladıktan sonra sistemi yeniden başlatın:
```bash
sudo reboot
```

## Sonuç
Yukarıdaki adımlar izlenerek `grub rescue>` hatası genellikle çözülür. Eğer sorun devam ederse, daha fazla inceleme yapılması gerekebilir. Bu durumda, disk yapılandırmasını veya işletim sistemini yeniden yüklemek gerekebilir.

## Ekstra Bilgiler
Bu hata ile ilgili daha fazla bilgi ve kaynak için GRUB belgelerini ziyaret edebilirsiniz.
