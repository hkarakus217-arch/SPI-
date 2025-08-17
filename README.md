# SPI-
SPI Protokolü

“Serial Peripheral Interface” olan SPI, tam çift yönlü (full-duplex) bir iletişim protokolüdür. Bu, veri gönderme ve alma işlemlerinin aynı anda gerçekleşebileceği anlamına gelir. İletişim, bir master cihaz ve bir veya daha fazla slave cihaz arasında gerçekleşir.

Master cihaz, iletişim kurmak istediği slave cihazı seçer ve bu seçimi genellikle SPI donanımında bulunan SS (Slave Select) pini aracılığıyla yapar. Master cihaz üzerindeki SS pini, kullanıcı tarafından atanır ve hangi slave cihazın aktif olduğunu belirlemek için kullanılır.

SPI’nin bir diğer önemli özelliği, slave cihazların seçilmesi ve yönetilmesinde esneklik sağlamasıdır. Bu özellik, SPI’yi genellikle I2C’den ayıran temel farklardan biridir.

SCLK : Serial Clock (output from master). :Senkron seri haberleşmesi için kullanılır. Haberleşme için kare dalga oluşturur. Yani SPI haberleşmesinde senkronu sağlayan saat bulundurur. Saat sinyali master cihaz tarafından üretilir.
MOSI : Master Output, Slave Input (output from master). Master’ın çıkış Slave’in giriş olduğu  veri yolunu oluşturur.
MISO : Master Input, Slave Output (output from slave). Master’ın giriş Slave’in çıkış olduğu veri yolunu oluşturur.
SS : Slave Select (active low, output from master).  Slave select anlamına gelir. Master cihazın Slave cihazları seçmesine yarar. Master’ın SS pinleri kontrol edilecek Slave cihaza göre seçilir ve kullanıcı tarafından belirlenir.
Seri Haberleşme Protokolleri seri haberleşme protokolleri,i2c,spi,uart
Veri iletimi 8-bit olarak gerçekleşir. CS pinini kullanarak slave seçimini yaptıktan sonra master cihazından göndermek istediğiniz veriyi MOSI pinini Lojik 0 ve Lojik 1 şeklinde binary olarak değiştirerek hatta yazarsınız. Her bir bit için CLK pinini 0 – 1 yapmanız yeterlidir. Aşağıdaki resimde daha net bir şekilde görülmektedir.

Seri Haberleşme Protokolleri seri haberleşme protokolleri,i2c,spi,uart
İletişimin SPI ile gerçekleşeceğini belirtmek için SPI kütüphanesi mikroişlemciye yüklenmesi gerekir.Kodları yazarken hem master hem de slave cihazlar için ayrı ayrı kod yazılır. SPI iletişim için Arduino da hazır bir kütüphane bulunmaktadır. Ancak bu kütüphane Arduino her zaman master konumda olacağı düşünülerek hazırlanmıştır.

Slave cihaza kod yazılırken SPI kütüphanesinin veri aktarımı için kullanılan registerlarda gerekli değişimler yapılır. Bu registerlar arduino için;

SPDR(SPI Data Register) : Bu register SPI’daki aktarılacak veriyi tutar.

SPSR(SPI Status Register): Bu register SPI durumunu belirtir. Bit kaydırmada aktarılacak veri olup olmadığını kontrol eder.

SPCR(SPI Control Register) : SPI başlangıç ayarlarının yapıldığı registerdır. Master Slave ayarları burada yapılır.
