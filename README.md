# Sound_analysis_and_digital_filter_design

### NOT:
Proje kodu(.rar dosyasında) 4 parttan oluşmaktadır. 

Akış diagramı:

Part 1, bağlama sesinin sönümlediğini göstermek için AGF tasarımını

Part 2, gitar sesinin sönümlediğini göstermek için YGF tasarımını

Part 3, ilk partta tasarlanan ve kullanılan AGF'yi hem bağlama hem de gitar üzerine uygulayıp, çıkışta bağlama sesinin bozulduğunu ama gitar sesinin bozulmaya uğramadığını

Part 4, ikinci partta tasarlanan ve kullanılan YGF'yi hem bağlama hem de gitar üzerine uygulayıp, çıkışta gitar sesinin bozulduğunu ama bağlama sesinin bozulmaya uğramadığını göstermek amaçlı olarak ayrılmıştır.

NOT: Partlar arasındaki geçişler, kodu tekrar çalışıtırmanız durumunda hata alınmaması için böyle düzenlendi.

### NOTE:
The projects code (.rar files) consists of 4 parts.

Flow diagram:

Part 1, AGF design to show that the sedge sound is damping

Part 2, YGF design to show that the guitar sound is damping

Part 3 applies the AGF designed and used in the first part to both the sedge and the guitar, and the sedge sound is distorted at the exit, but the guitar sound is not distorted

Part 4 applies the ygf designed and used in the second part to both the sedge and the guitar, and the guitar sound is distorted at the exit, but the sedge sound is not distorted. it is reserved for demonstration purposes.

Note: transitions between parts have been edited this way to avoid errors if you run the code again.

## ÖZET
Bu projede Python Programlama Dili ile ses analizi konusu üzerinde çalışılacaktır. Birbirinden farklı iki sesin (gitar ve bağlama) frekans uzayında genlik, enerji gibi bileşenleri incelenecektir. Uygun dijital filtreler tasarlanarak seslerin ayrımı yapılacaktır.

## 1. Giriş
Projede, birbirinden farklı iki sesin bilgisayar ortamında ayrımını yapabilmek amaçlanmıştır. Sesler, birbirlerinden farklı oldukları için farklı frekansa, genliğe veya enerjiye sahip olacaklardır. İlgili parametrelerden faydalanarak seslerin ayrı ayrı analizlerinin yapılması gerekecektir. Bu analizleri gerçekleştirebilmek için, çeşitli sayısal işaret işleme yöntemleri kullanılacaktır. Analizler sonucu uygun filtreleme tekniklerinden faydalanılarak, ihtiyaca uygun şekilde filtre tasarımı yapılıp, seslerin ayrımı sağlanmış olacaktır. Projede kullanılan ve ayrımı yapılacak olan ses grubu, gitar ve bağlamaya aittir.

## 2. Deneyler ve Analiz
Bilgisayar ortamında ses analizi için, Python Programlama Dili’nin bir aracı olan Jupyter Notebook kullanılacaktır. Analizlerin yapılabilmesi için, .wav formatındaki ses dosyaları Jupyter Notebook ortamına eklenmiştir. Uygun kod bloğu ile, ayrı ayrı eklenen ses dosyalarından ses işaretleri elde edilmiştir.
Ses işaretlerinin Fourier Dönüşümü alınarak frekans uzayında incelenme yapılmasına imkan sağlanmıştır. Elde edilen Fourier Dönüşümü’nden işaretlerin genlik grafiği çizdirilmiştir. İki farklı işaretin de genlik grafikleri karşılaştırılarak bir işaretin ciddi anlamda bozulmaya uğramadan geçtiği fakat diğer işaretin ise büyük oranda bozulmaya uğrayacağı durumlar düşünülerek filtre tasarımı gerçekleştirilmiştir. Yani, her bir işarete özel filtre tasarlanmıştır.

Filtre tasarımı, Python tabanlı bir GUI (Graphical User Interface) olan pyFDA ile, işaretin yoğunlukta bulunduğu değer aralıkları ve o değer aralıklarında almış olduğu genlik değerleri gibi parametreler göz önünde bulundurularak yapılmıştır. Tasarlanan filtreler her iki ses işareti için de denenmiş ve işarete uygun filtreden, o ses işaretinin geçtiği gözlemlenmiştir.

Ayrık zamanlı işaretler tasarlanan filtrelerden geçirildikten sonra, çıkış işaretlerinin Fourier Dönüşümleri alınmıştır. Fourier Dönüşümleri’nden elde edilen genlik spektrumlarına göre, işaretlerin enerjisi hesaplanmıştır.
Her ses grubu için ayrı ayrı analizler yapılmıştır. İlgili grafik ve filtre çıktıları ile tasarlanan filtrelerin parametreleri “2.1 Grafik, Tablo ve Şekiller” başlığı altında görülmektedir.

#### 2.1. Birinci Ses Grubu (Leyla the Band – Yokluğunda)

1.ses grubundaki gitar ve bağlamaya ait ses işaretlerinin frekans cevaplarının genlik grafikleri Şekil 1 ve Şekil 2’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939265-3b95489e-4dd6-4522-9a44-6008cce11c17.png)
![image](https://user-images.githubusercontent.com/70964563/152939291-47ba9ee1-48cb-4fe2-b5d6-d0a0c2d0c378.png)

1.ses grubu için bağlama sesinin yüksek oranda bozulmaya uğramadan geçtiği, lakin gitar sesinin bozulmaya uğradığı filtrenin, yüksek geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 3’te görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939352-3a076b58-ce26-4eda-b8d3-a84309cc3c96.png)

1.ses grubu için tasarlanan yüksek geçiren filtrenin parametreleri aşağıda verilen tabloda (Tablo 1.) görülmektedir:

![image](https://user-images.githubusercontent.com/70964563/152940831-1ed9581a-ea4a-450e-914c-461c4ece830d.png)

Yüksek geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 4 ve Şekil 5’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939525-5cabe2de-f0a1-4663-a4ae-a62ac87d9629.png)
![image](https://user-images.githubusercontent.com/70964563/152939559-da2dc1a1-9ca7-4a14-911d-b92b6be498a2.png)

1.ses grubu için gitar sesinin yüksek oranda bozulmaya uğramadan geçtiği fakat bağlama sesinin ciddi seviyede bozulmaya uğradığı filtrenin, alçak geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 6’da görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939619-3b5395a0-cf6e-4641-92e5-82454b38e6c4.png)

1.ses grubu için tasarlanan alçak geçiren filtrenin parametreleri aşağıda verilen tabloda (Tablo 2.) görülmektedir:

![image](https://user-images.githubusercontent.com/70964563/152940911-1a97d7e7-cfce-48aa-9a3e-4ac5244c45b2.png)

Alçak geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 7 ve Şekil 8‘de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939656-b79651bc-cb5e-4c8b-a9aa-2aad86a4be4c.png)
![image](https://user-images.githubusercontent.com/70964563/152939689-b0b45357-5c46-4416-b7c5-bbd3dc6871b6.png)



#### 1. Ses grubu için sonuçların analizi:

1.bağlama sesini 1.gitar sesinden ayırt etmek için tasarlanan yüksek geçiren filtreden geçirilen ses işaretlerinin enerjileri ve bu enerjiler arasındaki fark, aşağıda görüldüğü gibidir:
Gitar sesi enerjisi: 1.716972878405396 Joule
Bağlama sesi enerjisi: 2.7013771588096795 Joule
Enerjiler arasındaki fark: 0.9844042804042836 Joule

Sonuçlar incelendiğinde bağlama sesinin enerjisinin gitar sesinin enerjisine göre yüksek kaldığı görülmektedir.

1.gitar sesini 1.bağlama sesinden ayırt etmek için tasarlanan alçak geçiren filtreden geçirilen ses işaretlerinin enerjileri ve bu enerjiler arasındaki fark, aşağıda görüldüğü gibidir:
Gitar sesi enerjisi: 21.365604998855453 Joule
Bağlama sesi enerjisi 2.847591033916202 Joule
Enerjiler arasındaki fark: 18.51801396493925 Joule

Sonuçlar incelendiğinde gitar sesinin enerjisinin bağlama sesinin enerjisine göre oldukça yüksek kaldığı görülmektedir.



----------------------------------------------------------------------------------------------------------------------------------------------------------------


#### 2.2. İkinci Ses Grubu (Serkan Nişancı – Farketmez Hesaplaşırız)

2.ses grubundaki gitar ve bağlamaya ait ses işaretlerinin frekans cevaplarına ait genlik grafikleri Şekil 9 ve Şekil 10’da görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939819-fdeb8df1-a4e7-4791-8c59-8b03da4808fd.png)
![image](https://user-images.githubusercontent.com/70964563/152939848-3c68cd78-f752-4cbb-aaf4-da3f724933b6.png)


2.ses grubu için bağlama sesinin yüksek oranda bozulmaya uğramadan geçtiği ama gitar sesinin bozulmaya uğradığı filtrenin, alçak geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 11’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939894-66e20460-4883-46fa-b55b-6efcbee62060.png)

2.ses grubu için tasarlanan alçak geçiren filtrenin parametreleri aşağıda verilen tabloda (Tablo 3.) görülmektedir:

![image](https://user-images.githubusercontent.com/70964563/152942560-eb931d34-9e36-4088-9dbd-6f9728d424df.png)

Alçak geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 12 ve Şekil 13’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940097-cb3493a6-6ad9-4655-8325-951f273121cd.png)
![image](https://user-images.githubusercontent.com/70964563/152940131-c43f1386-a0a3-4dca-95c3-42b4060d9332.png)


2.ses grubu için gitar sesinin yüksek oranda bozulmaya uğramadan geçtiği, lakin bağlama sesinin bozulmaya uğradığı filtrenin, yüksek geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 14’te görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940178-13082ebb-3ed9-489b-a7f6-d16b8281ec45.png)

2.ses grubu için tasarlanan yüksek geçiren filtrenin parametreleri aşağıda verilen tabloda (Tablo 4.) görülmektedir:

![image](https://user-images.githubusercontent.com/70964563/152942649-310ca091-c515-4986-a6c9-969fca68bbda.png)

Yüksek geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 15 ve Şekil 16‘da görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940211-901197a1-a7e9-4b64-b7f9-647741886e70.png)
![image](https://user-images.githubusercontent.com/70964563/152940228-d9c19b62-f216-442c-b224-63609432110d.png)


#### 2. Ses grubu için sonuçların analizi:

2.bağlama sesini 2.gitar sesinden ayırt etmek için tasarlanan alçak geçiren filtreden geçirilen ses işaretlerinin enerjileri ve bu enerjiler arasındaki fark, aşağıda görüldüğü gibidir:

Gitar sesi enerjisi: 9.253783251498717 Joule
Bağlama sesi enerjisi: 15.5124538255554886 Joule
Enerjiler arasındaki fark: 6.258755004056169 Joule

Sonuçlar incelendiğinde bağlama sesinin enerjisinin gitar sesinin enerjisine göre yüksek kaldığı görülmektedir.

2.gitar sesini 2.bağlama sesinden ayırt etmek için tasarlanan yüksek geçiren filtreden geçirilen ses işaretlerinin enerjileri ve bu enerjiler arasındaki fark, aşağıda görüldüğü gibidir:

Gitar sesi enerjisi: 5.783171688743165 Joule
Bağlama sesi enerjisi 1.1893705711576523 Joule
Enerjiler arasındaki fark: 4.6138011175855125 Joule

Sonuçlar incelendiğinde gitar sesinin enerjisinin bağlama sesinin enerjisine göre yüksek kaldığı görülmektedir.


----------------------------------------------------------------------------------------------------------------------------------------------------------------



#### 2.3. Üçüncü Ses Grubu (Müslüm Gürses – İtirazım Var)
3.ses grubundaki gitar ve bağlamaya ait ses işaretlerinin frekans cevaplarına ait genlik grafikleri Şekil 17 ve Şekil 18’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940467-5c878adc-2de7-4241-a3a4-5febdf51a7aa.png)
![image](https://user-images.githubusercontent.com/70964563/152940491-a4529472-99b1-4107-aa45-1edd9a41b875.png)

3.ses grubu için bağlama sesinin yüksek oranda bozulmaya uğramadan geçtiği, ancak gitar sesinin bozulmaya uğradığı filtrenin, yüksek geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 19’te görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940514-33214117-85ec-460a-9bf6-88902c2985c8.png)

3.ses grubu için tasarlanan yüksek geçiren filtrenin parametreleri aşağıda verilen tabloda (Tablo 5.) görülmektedir:

![image](https://user-images.githubusercontent.com/70964563/152942959-7aa24dd1-2bf5-4dd1-a4bf-8bcb0f5f531e.png)

Yüksek geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 20 ve Şekil 21’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940547-61ab789b-7663-42a1-9221-c20863bcf294.png)
![image](https://user-images.githubusercontent.com/70964563/152940575-0bd658dd-152c-4f7b-ab4c-640d1cef3361.png)

3.ses grubu için gitar sesinin yüksek oranda bozulmaya uğramadan geçtiği, oysaki bağlama sesinin ciddi seviyede bozulmaya uğradığı filtrenin, alçak geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 22’da görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940629-d88f0cb1-bd73-4138-b726-aa3ba3398fd1.png)

3.ses grubu için tasarlanan alçak geçiren filtrenin parametreleri aşağıda verilen tabloda (Tablo 6.) görülmektedir:

![image](https://user-images.githubusercontent.com/70964563/152943029-d1c3425b-2123-41f6-a17e-a5f1184cb7f0.png)

Alçak geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 23 ve Şekil 24‘de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940658-a1cfb9b9-fb7d-42d0-82da-dee321c2931e.png)
![image](https://user-images.githubusercontent.com/70964563/152940683-9289c073-01c3-4b27-acca-b6ac05888221.png)

#### 3. Ses grubu için sonuçların analizi:

3.bağlama sesini 3.gitar sesinden ayırt etmek için tasarlanan yüksek geçiren filtreden geçirilen ses işaretlerinin enerjileri ve bu enerjiler arasındaki fark, aşağıda görüldüğü gibidir:

Gitar sesi enerjisi: 0.4908210972341997 Joule
Bağlama sesi enerjisi: 9.188821906636914Joule
Enerjiler arasındaki fark: 8.698000809402714 Joule

Sonuçlar incelendiğinde bağlama sesinin enerjisinin gitar sesinin enerjisine göre yüksek kaldığı görülmektedir.

3.gitar sesini 3.bağlama sesinden ayırt etmek için tasarlanan alçak geçiren filtreden geçirilen ses işaretlerinin enerjileri ve bu enerjiler arasındaki fark, aşağıda görüldüğü gibidir:

Gitar sesi enerjisi: 27.40048824779398 Joule
Bağlama sesi enerjisi 3.2728820435684467 Joule
Enerjiler arasındaki fark: 24.127606204225533 Joule

Sonuçlar incelendiğinde gitar sesinin enerjisinin bağlama sesinin enerjisine göre oldukça yüksek kaldığı görülmektedir.


----------------------------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------------------------


### 3. Sonuç ve Yorum
Ses işaretlerinin frekans uzayındaki spektrumlarının incelenerek yapılan gözlemler sonucu uygun filtre seçimi ve bu filtrenin parametrelerinin belirlenmesi konusunda deneyim sahibi olundu.

Her bir ses işaretine özel filtre tasarlandıktan sonra, bu filtrelerden aynı ses grubundaki bir diğer işaretin geçirilmesi için birden çok parametre ile çözüm önerisinde bulunuldu. Bu çözümler pyFDA üzerinde denenerek ilgili filtrenin testi sağlandı. En uygun sonuçları veren parametreler filtrenin tasarımında kullanıldı.

Her bir ses işaretinin birden fazla filtre üzerinde denenmesinden dolayı çözüm önerilerindeki ortaya çıkan parametre fazlalığı, sağladığı avantajların yanı sıra sürecin uzamasına ve karmaşık hale gelmesine sebebiyet verdiği için işlemleri zorlaştırmıştır.
Python tabanlı, ses ve müzik analizi için kullanılan Librosa paketi içerisinde bulunan Spektogram[1] ile daha hassas veriler elde dilip buna uygun filtreler tasarlanabilirdi.

Bu çalışmada, gözlemlenen genlik spektrumlarına uygun olarak filtre tasarlanması, birbirinden farklı seslerin tasarlanmış filtreler ile ayrımının yapılması öğrenilmiştir. Analiz yapma konusunda ve ihtiyaç doğrultusunda uygun parametrelerin kullanılması ve bunların testinin gerçekleştirilmesi konusunda da bilgi sahibi olundu.

[1]Spektogram: Belirli bir dalga formunda bulunan çeşitli frekanslarda bir sinyalin sinyal gücünü veya yüksekliğini temsil eden görseldir. Aynı zamanda enerji seviyelerini zaman içinde nasıl değiştiğini de gösterir.


#### 3.1 Karşılaştırmalar ve Sürpriz Sonuçlar

Her bir gruptaki gitar seslerine özel tasarlanan filtreler, bağlama sesleri üzerinde de denenmiş ve çıkış işaretleri karşılaştırılmıştır. Ayrıca gitar sesleri de bağlama seslerine özel tasarlanan filtrelerden geçirilmiş ve çıkış işaretleri karşılaştırılmıştır.

Birinci ses grubu için, yüksek geçiren filtre çıkışında gitar sesine ait enerji ile bağlama sesine ait enerjilerin birbirine yakın olduğu görülmüştür.
İkinci ses grubu için tasarlanan filtre yapılarının, birinci ses grubu için tasarlanan filtreler ile karşılaştırıldığında, tam zıt filtre yapılarına sahip olması gerektiği anlaşılmıştır.

Örneğin, birinci ses grubundaki gitar sesini elde etmek için AGF tasarlanırken, ikinci ses grubundaki gitar sesini elde etmek için YGF tasarlanmıştır.
Üçüncü ses grubundaki bağlama sesi için tasarlanan YGF ikinci ses grubundaki gitar sesi için tasarlanan YGF ile aynı parametrelere sahiptir.

Sonuç olarak birbirinden farklı yapılara/parametrelere sahip 5 adet filtre tasarımı gerçekleştirilmiştir.

----------------------------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------------------------
### 4. Akış Şeması
![image](https://user-images.githubusercontent.com/70964563/152944088-b5c0a2d3-ba9c-44c7-83d7-f091644a61b4.png)
