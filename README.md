# Raspberry Pi Pico as a Rubber Ducky 

![2022-02-09-16-58-32_Trim](https://user-images.githubusercontent.com/29992381/153216687-11a80cd9-38f5-4b8a-b247-9fe963997136.gif)


## Kurulum

1) Raspberry Pi Pico cihazınız için CircuitPython'u [indirin](https://circuitpython.org/board/raspberry_pi_pico/). 
2) Boot düğmesine basılı tutarken cihazı bir USB bağlantı noktasına takın ve cihazı taktıktan sonra boot tuşundan elinizi çekin. Bunun sonucunda "RPI-RP2" adlı çıkarılabilir bir medya aygıtı karşınıza çıkacaktır.
3) İndirdiğiniz .uf2 dosyasını Pico'nun (RPI-RP2) ana dizinine kopyalayın. Bir süre sonra cihaz yeniden başlayacak ve 1-2 saniye sonra CIRCUITPY adında çıkarılabilir bir medya aygıtı olarak karşınıza çıkacaktır.
4) Ardından [adafruit-circuitpython-bundle-7.x-mpy-YYYYMMDD.zip](https://github.com/adafruit/Adafruit_CircuitPython_Bundle/releases/latest) dosyasını indirin ve cihazın dışına çıkarın. 
5) adafruit-circuitpython-bundle-7.x-mpy-YYYYMMDD klasörü altındaki "lib" klasörüne gidin ve "adafruit_hid'i" Raspberry Pi Pico'nuzdaki lib klasörüne kopyalayın.
6) [Buradaki](https://raw.githubusercontent.com/dbisu/pico-ducky/main/duckyinpython.py) sayfaya giderek CTRL + S tuşlarına basın ve dosyayı Pico'nun içerisinde bulunan code.py dosyasının üzerine yazarak Raspberry Pi Pico'nun ana dizinine "code.py" olarak kaydedin.
7) [Buradaki](https://github.com/hak5darren/USB-Rubber-Ducky/wiki/Payloads) linkten bir script bulun veya kendi Rubber Ducky scriptinizi [oluşturun](https://github.com/hak5darren/USB-Rubber-Ducky/wiki/Duckyscript) ve "payload.dd" olarak kaydedin.
8) Dikkat edin, son işlemden sonra cihaz yeniden başlatılacak ve yarım saniye sonra komut dosyası (payload.dd) çalışacaktır.

## USB Etkinleştirme/Devre Dışı Bırakma

Pico'nun gizlilik amacıyla bir USB depolama aygıtı gibi görünmemesine istiyorsanız;
1) Cihazı USB bağlantı noktasına takın.
2) "boot.py" dosyasını Pico'nun (RPI-RP2) ana dizinine kopyalayın.
3) payload.dd dosyanızı da Pico'ya (RPI-RP2) kopyalayın.
4) Pico'yu bilgisayarınızdan çıkarın. Pin 18 ve pin 20 arasına bir jumper kablosu bağlayın. Bu durum Pico üzerinde bir kısa devre yaratacaktır ve hedef bilgisayara takıldığında Pico'nun bir USB sürücüsü olarak görünmesini engelleyecek.
5) Tekrar programlamak için (Payload'ınızı güncellemek için) jumper kabloyu çıkarın ve PC'nize yeniden bağlayın. Varsayılan modda, USB depolama aygıtı aktif durumda olacaktır.

![1](https://user-images.githubusercontent.com/29992381/153219218-98d55417-4d9f-45a9-bbdf-1d719625b41d.jpg)


## Klavye Düzenlerini Değiştirme

Varsayılan modda klavye düzeni İngilizce'dir. Bunu değiştirmek isterseniz;
1) https://kbdlayout.info/ sayfasından istediğiniz klavye düzenini bularak üzerine tıklayın ve linki kopyalayıp https://www.neradoc.me/layouts/ sayfasındaki kutucuğa yapıştırın. Ardından "Make Zip Bundle Links" butonuna tıklayın.
2) Ardından "Download the zip file (.py)" butonuna tıklayın.
3) İndirilen dosyanın içerisinden kendize uygun olan klavye düzeninin dosyalarını Pico'nuzun içerisindeki lib klasörü altına kopyalayın (ben Türkçe Q klavye düzenini tercih ediyorum);
- keyboard_layout.mpy
- keyboard_layout_win_tuq.mpy
- keycode_win_tuq.mpy

![2](https://user-images.githubusercontent.com/29992381/153212715-a0efbc44-1b14-41aa-8f2b-da8b7e0c4ab9.png)

## Dil Dosyanızı Kullanmak için Pico Kodunuzu Değiştirin

Pico içerisindeki "code.py" dosyasını açın ve içerisindeki şu kodu;
```python
from adafruit_hid.keyboard_layout_us import KeyboardLayoutUS as KeyboardLayout
from adafruit_hid.keycode import Keycode
```

aşağıdaki kod ile değiştirin;

```python
from keyboard_layout_win_tuq import KeyboardLayout
from keycode_win_tuq import Keycode
```

## Raspberry Pi Pico'nun Son Hali


![y-geometri-Ozel-Dortgenler-–-Eskenar-Dortgen-Dikdortgen-Kare-ve-Deltoid (1)](https://github.com/furkan-enes-polatoglu/RaspberryPico-as-a-RubberDucky/assets/29992381/91897a5c-c782-4774-9cdc-1f5e554f57ef)



