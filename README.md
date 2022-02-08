# Sound_analysis_and_digital_filter_design

### NOT:
Proje 4 parttan oluşmaktadır.
Akış diagramı:
Part 1, bağlama sesinin sönümlediğini göstermek için AGF tasarımını
Part 2, gitar sesinin sönümlediğini göstermek için YGF tasarımını
Part 3, ilk partta tasarlanan ve kullanılan AGF'yi hem bağlama hem de gitar üzerine uygulayıp, çıkışta bağlama sesinin bozulduğunu ama gitar sesinin bozulmaya uğramadığını
Part 4, ikinci partta tasarlanan ve kullanılan YGF'yi hem bağlama hem de gitar üzerine uygulayıp, çıkışta gitar sesinin bozulduğunu ama bağlama sesinin bozulmaya uğramadığını
göstermek amaçlı olarak ayrılmıştır.
NOT: Partlar arasındaki geçişler, kodu tekrar çalışıtırmanız durumunda hata alınmaması için böyle düzenlendi.

### NOTE:
The project consists of 4 parts.
Flow diagram:
Part 1, AGF design to show that the sedge sound is damping
Part 2, YGF design to show that the guitar sound is damping
Part 3 applies the AGF designed and used in the first part to both the sedge and the guitar, and the sedge sound is distorted at the exit, but the guitar sound is not distorted
Part 4 applies the ygf designed and used in the second part to both the sedge and the guitar, and the guitar sound is distorted at the exit, but the sedge sound is not distorted
it is reserved for demonstration purposes.
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

#### • Birinci Ses Grubu (Leyla the Band – Yokluğunda)

1.ses grubundaki gitar ve bağlamaya ait ses işaretlerinin frekans cevaplarının genlik grafikleri Şekil 1 ve Şekil 2’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939265-3b95489e-4dd6-4522-9a44-6008cce11c17.png)
![image](https://user-images.githubusercontent.com/70964563/152939291-47ba9ee1-48cb-4fe2-b5d6-d0a0c2d0c378.png)

1.ses grubu için bağlama sesinin yüksek oranda bozulmaya uğramadan geçtiği, lakin gitar sesinin bozulmaya uğradığı filtrenin, yüksek geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 3’te görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939352-3a076b58-ce26-4eda-b8d3-a84309cc3c96.png)

1.ses grubu için tasarlanan yüksek geçiren filtrenin parametreleri aşağıda verilen tabloda (Tablo 1.) görülmektedir:

![image](https://user-images.githubusercontent.com/70964563/152940831-1ed9581a-ea4a-450e-914c-461c4ece830d.png)

1.ses grubu için tasarlanan alçak geçiren filtrenin parametreleri aşağıda verilen tabloda (Tablo 2.) görülmektedir:

![image](https://user-images.githubusercontent.com/70964563/152940911-1a97d7e7-cfce-48aa-9a3e-4ac5244c45b2.png)

Yüksek geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 4 ve Şekil 5’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939525-5cabe2de-f0a1-4663-a4ae-a62ac87d9629.png)
![image](https://user-images.githubusercontent.com/70964563/152939559-da2dc1a1-9ca7-4a14-911d-b92b6be498a2.png)

1.ses grubu için gitar sesinin yüksek oranda bozulmaya uğramadan geçtiği fakat bağlama sesinin ciddi seviyede bozulmaya uğradığı filtrenin, alçak geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 6’da görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939619-3b5395a0-cf6e-4641-92e5-82454b38e6c4.png)


Alçak geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 7 ve Şekil 8‘de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939656-b79651bc-cb5e-4c8b-a9aa-2aad86a4be4c.png)
![image](https://user-images.githubusercontent.com/70964563/152939689-b0b45357-5c46-4416-b7c5-bbd3dc6871b6.png)




#### • İkinci Ses Grubu (Serkan Nişancı – Farketmez Hesaplaşırız)

2.ses grubundaki gitar ve bağlamaya ait ses işaretlerinin frekans cevaplarına ait genlik grafikleri Şekil 9 ve Şekil 10’da görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939819-fdeb8df1-a4e7-4791-8c59-8b03da4808fd.png)
![image](https://user-images.githubusercontent.com/70964563/152939848-3c68cd78-f752-4cbb-aaf4-da3f724933b6.png)


2.ses grubu için bağlama sesinin yüksek oranda bozulmaya uğramadan geçtiği ama gitar sesinin bozulmaya uğradığı filtrenin, alçak geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 11’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152939894-66e20460-4883-46fa-b55b-6efcbee62060.png)

Alçak geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 12 ve Şekil 13’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940097-cb3493a6-6ad9-4655-8325-951f273121cd.png)
![image](https://user-images.githubusercontent.com/70964563/152940131-c43f1386-a0a3-4dca-95c3-42b4060d9332.png)


2.ses grubu için gitar sesinin yüksek oranda bozulmaya uğramadan geçtiği, lakin bağlama sesinin bozulmaya uğradığı filtrenin, yüksek geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 14’te görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940178-13082ebb-3ed9-489b-a7f6-d16b8281ec45.png)

Yüksek geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 15 ve Şekil 16‘da görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940211-901197a1-a7e9-4b64-b7f9-647741886e70.png)
![image](https://user-images.githubusercontent.com/70964563/152940228-d9c19b62-f216-442c-b224-63609432110d.png)


#### • Üçüncü Ses Grubu (Müslüm Gürses – İtirazım Var)
3.ses grubundaki gitar ve bağlamaya ait ses işaretlerinin frekans cevaplarına ait genlik grafikleri Şekil 17 ve Şekil 18’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940467-5c878adc-2de7-4241-a3a4-5febdf51a7aa.png)
![image](https://user-images.githubusercontent.com/70964563/152940491-a4529472-99b1-4107-aa45-1edd9a41b875.png)

3.ses grubu için bağlama sesinin yüksek oranda bozulmaya uğramadan geçtiği, ancak gitar sesinin bozulmaya uğradığı filtrenin, yüksek geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 19’te görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940514-33214117-85ec-460a-9bf6-88902c2985c8.png)

Yüksek geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 20 ve Şekil 21’de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940547-61ab789b-7663-42a1-9221-c20863bcf294.png)
![image](https://user-images.githubusercontent.com/70964563/152940575-0bd658dd-152c-4f7b-ab4c-640d1cef3361.png)

3.ses grubu için gitar sesinin yüksek oranda bozulmaya uğramadan geçtiği, oysaki bağlama sesinin ciddi seviyede bozulmaya uğradığı filtrenin, alçak geçiren filtre olmasına karar verilmiştir. pyFDA arayüzünde tasarlanan filtrenin şekli Şekil 22’da görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940629-d88f0cb1-bd73-4138-b726-aa3ba3398fd1.png)

Alçak geçiren filtrenin çıkışında görülen işaretlerin frekans cevaplarına ait genlik grafikleri, Şekil 23 ve Şekil 24‘de görülmektedir.

![image](https://user-images.githubusercontent.com/70964563/152940658-a1cfb9b9-fb7d-42d0-82da-dee321c2931e.png)
![image](https://user-images.githubusercontent.com/70964563/152940683-9289c073-01c3-4b27-acca-b6ac05888221.png)




