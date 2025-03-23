# Metro Simülasyonu Projesi
Bu proje, metropol metro ağı üzerinde en az aktarma ve en hızlı rotayı bulma simülasyonunu gerçekleştiren bir Python programıdır. 
BFS ve A* algoritmaları kullanılarak, kullanıcıların belirli iki istasyon arasında en az aktarma yaparak en kısa sürede hedefe ulaşmaları amaçlanmıştır.

## Kullanılan Teknolojiler ve Kütüphaneler
- **Python 3.x**: Programlama dili olarak Python kullanılmıştır.
- **heapq**: A* algoritması için öncelik sıralı kuyruğun yönetilmesi için kullanılmıştır.
- **collections**: BFS (Breadth-First Search) algoritmasında kullanılan `deque` ve `defaultdict` sınıfları ile veri yapılarını yönetmek için kullanılmıştır.
  
### Kullanılan Ana Kütüphaneler:
- defaultdict: Sözlük yapısını temel alır ancak anahtar yoksa varsayılan bir değer döndürür.
- deque: FIFO (First In First Out) veri yapısına sahip bir kuyruğun hızlı bir şekilde yönetilmesi için kullanılır.
- heapq: A* algoritmasında öncelik sırasına göre elemanları sıralamak için kullanılır.
- typing: Python'un tip ipuçları modülüdür. Kodun daha okunabilir ve hatasız olmasını sağlamak için Dict, List, Set, Tuple ve Optional gibi veri tipleri kullanıldı.

## Algoritmaların Çalışma Mantığı

### BFS (Breadth-First Search) Algoritması:
BFS algoritması, **en az aktarma** gerektiren rotayı bulmak için kullanılır.
Bu algoritma, ilk önce başlangıç istasyonundan en yakın komşu istasyonlara gider, ardından bu komşulardan daha uzak olanlara geçer. 
BFS, her bir istasyonun sadece bir kez ziyaret edilmesini sağlar, böylece en kısa rotayı bulur.

#### Nasıl Çalışır:
1. Başlangıç istasyonundan hedef istasyona kadar olan yol, komşu istasyonları keşfederek genişler.
2. Her adımda, keşfedilen istasyonların aktarma sayısı takip edilir.
3. İlk olarak hedef istasyon bulunursa, rota döndürülür.

### A* (A Star) Algoritması:
A* algoritması, **en hızlı rota**yi bulmak için kullanılır. 
Bu algoritma, her adımda toplam süreyi ve hedef istasyona olan tahmin edilen mesafeyi dikkate alarak en verimli rotayı arar. 
`heapq` (öncelik kuyruğu) kullanılarak, her zaman en düşük toplam süreye sahip istasyon seçilir.

#### Nasıl Çalışır:
1. Başlangıç noktasından hedef istasyona kadar olan rotalar, geçiş süreleri dikkate alınarak hesaplanır.
2. A* algoritması, her istasyon için toplam süreyi hesaplar ve hedefe daha yakın istasyonları öncelikli olarak keşfeder.
3. Hedef istasyon bulunursa, rota ve toplam süre döndürülür.

## Neden Bu  Alagoritmalar Kullanıldı:

### BFS (Breadth-First Search):
BFS, genellikle en kısa yol veya en az sayıda aktarma gerektiren yolları bulmak için kullanılır. 
Metro hattı gibi yapılar, bir noktadan başka bir noktaya ulaşırken belirli bir sıra ile geçilmesi gereken çok sayıda istasyon içerir. 
BFS algoritması, her bir istasyonu birer birer keşfederek, ilk defa hedefe ulaşan yolun en az aktarma gerektiren yol olduğunu garanti eder. 
Bu yüzden, "en az aktarma" problemini çözmek için uygun bir seçimdir.

### A* (A-Star) Algoritması:
A* algoritması, en hızlı yolu bulmak için idealdir çünkü hem geçmişteki mesafeyi (yol uzunluğu) hem de gelecekteki olasılıkları (hedefe olan mesafe) dikkate alır. 
Bu sayede, sadece en kısa değil, aynı zamanda en hızlı yolu da bulmak mümkün olur. 
Metro hatlarında, aktarma sayısının değil, yolculuk süresinin önemli olduğu durumlarda A* algoritması daha iyi bir seçimdir.

## Örnek Kullanım ve Test Sonuçları
Projenin işlevselliğini test etmek için, aşağıdaki gibi birkaç test senaryosu oluşturulmuştur:

### Senaryo 1: AŞTİ'den OSB'ye
**En az aktarmalı rota**: AŞTİ → Kızılay → Ulus → Demetevler → OSB
**En hızlı rota**: AŞTİ → Kızılay → Ulus → Demetevler → OSB (10 dakika)

### Senaryo 2: Batıkent'ten Keçiören'e
**En az aktarmalı rota**: Batıkent → Demetevler → Gar → Keçiören
**En hızlı rota**: Batıkent → Demetevler → Gar → Keçiören (14 dakika)

### Senaryo 3: Keçiören'den AŞTİ'ye
**En az aktarmalı rota**: Keçiören → Gar → Sıhhiye → AŞTİ
**En hızlı rota**: Keçiören → Gar → Sıhhiye → AŞTİ (12 dakika)

## Projeyi Geliştirme Fikirleri
Bu projeyi daha verimli ve kullanıcı dostu hale getirmek için aşağıdaki geliştirmeler yapılabilir:
1. **Kullanıcı Arayüzü (GUI)**: Kullanıcıların harita üzerinde istasyonları seçebileceği ve rotaları görsel olarak takip edebileceği bir arayüz oluşturulabilir.
2. **Farklı Algoritmaların Kullanımı**: Farklı rotalama algoritmaları (örneğin, Dijkstra) eklenebilir.
3. **Dinamik Zaman Geliştirmeleri**: Metro hatlarındaki sefer sıklığına göre dinamik süreler eklenebilir.
4. **API Entegrasyonu**: Gerçek zamanlı verilerle entegre olarak, sistem güncel metro hat bilgilerini alabilir.
5. **Testlerin Geliştirilmesi**: Daha fazla senaryo ve test ekleyerek algoritmaların farklı durumlarda nasıl performans gösterdiği gözlemlenebilir.
