# Java-da S.O.L.I.D prinsipləri

Burada proqramlaşdırma sahəsində "yaxşı kod" yazmaq üçün ümumi olaraq qəbul edilmiş prinsiplər öz əksini tapmışdır.

## SOLID

SOLID prinsipləri ümumiləşdirilərək Robert C. Martin tərəfindən irəli sürülmüşdür.Michael Feathers isə SOLID abbreviaturası ilə bu prinsipləri qısa şəkildə ifadə etmişdir.

SOLID:
- kodu daha çevik olmasını, 
- kodun təkrar istifadəsini, inkişafa davamlı, saxlanıla bilən olmasını 
- rahat başa düşülən olmasını, 
- təkrarların qarşısının alınmasını
təmin edən prinsiplər toplusudur. 

#### Tək Cavabdehlik prinsipi (Single-responsibility principle)

Hər bir sinif sadəcə bir funksionallığı təmsil etməlidir. Başqa sözlə tək məqsədli olmalıdır. Gəlin prinsipi pozan kod nümunəsinə baxaq:

<a href="https://im.ge/i/Fa6XSF"><img src="https://i.im.ge/2022/07/23/Fa6XSF.md.png" alt="Fa6XSF.md.png" border="0"></a>

Gördüyümüz kimi Masin sinfinin iki müxtəlif metodu, yəni funksiomallığı var. Bunun yerinə iki ayrı sinif yaratmaq prinsip baxımından məqsədə uyğundur.

#### Açıq-qapalı prinsipi (Open-closed principle)

Proqram təminatı obyektləri (məsələn, siniflər, modullar, funksiyalar) genişləndirmə üçün `açıq`, lakin dəyişiklik üçün `qapalı` olmalıdır.

Gəlin aşağıdakı nümunə üzərindən izah edək:

<a href="https://im.ge/i/Fa61gh"><img src="https://i.im.ge/2022/07/23/Fa61gh.md.png" alt="Fa61gh.md.png" border="0"></a>

Tutaq ki, biz indi QırxAyaq adlı başqa bir alt sinif əlavə etmək istəsək şərt hissəsində dəyişiklik etməli olacağıq. Bu da Açıq-Qapalı Prinsipinə zidd olacaq. Bəs necə etməliyik deyə sual ortaya çıxacaq.  başqa if ifadəsi əlavə etməklə yuxarıdakı sinfi dəyişdirməli olacağıq.
Bunun üçün üç ayrı sinif (Dovshan, Toyuq, QirxAyaq) yaradıb Ayaqlar sinifindən miras almaqla ayaqlariSay metodunu `override*` etməliyik:

<a href="https://im.ge/i/Fa6SMM"><img src="https://i.im.ge/2022/07/23/Fa6SMM.md.png" alt="Fa6SMM.md.png" border="0"></a>

<a href="https://im.ge/i/Fa6h51"><img src="https://i.im.ge/2022/07/23/Fa6h51.png" alt="Fa6h51.png" border="0"></a>

<a href="https://im.ge/i/Fa65Mm"><img src="https://i.im.ge/2022/07/23/Fa65Mm.png" alt="Fa65Mm.png" border="0"></a>

<a href="https://im.ge/i/Fa6IVp"><img src="https://i.im.ge/2022/07/23/Fa6IVp.png" alt="Fa6IVp.png" border="0"></a>

#### Liskov əvəzetmə prinsipi (Liskov substitution principle)

Kodumuzda heç bir dəyişiklik etmədən `alt sinif` miras aldığı `üst sinfin` xüsusiyyətlərini istifadə edərək onu əvəz etməlidir.
Tutaq ki, tutuquşu və dəvəquşu `alt siniflərimiz` var. `Üst sinif` olaraq da Quşlar sinfi var. Hər bir alt sinif üst sinfin xüsusiyyətlərini eynilə istifadə edəbilməlidir. Gəlin bunu aşağıdakı kod nümunəsilə göstərək:

<a href="https://im.ge/i/Fa69Ir"><img src="https://i.im.ge/2022/07/23/Fa69Ir.png" alt="Fa69Ir.png" border="0"></a>

Quslar üst sinfinin `qanadlar()` və `dimdik()` metodları vardır. Deməli hər bir alt sinif bunları eyni funksionallıqla istifadə edə bilməlidir.

<a href="https://im.ge/i/Fa6mJ0"><img src="https://i.im.ge/2022/07/23/Fa6mJ0.png" alt="Fa6mJ0.png" border="0"></a>

Tutuquşu sinfi Quslar sinfindən miras alaraq onun xüsusiyyətlərini istifadə etmişdir. Ayrıca özünə xas olan `danisma()` metoduna da malikdir.

<a href="https://im.ge/i/Fa6yrG"><img src="https://i.im.ge/2022/07/23/Fa6yrG.png" alt="Fa6yrG.png" border="0"></a>

Devequsu alt sinfi də Quslar sinfinin xüsusiyyətlərini eyni ilə istifadə etmişdir. O da özünə xas olan `ucmaq()` metoduna malikdir.

#### İnterfeys ayrılma prinsipi (Interface Segregation Principle (ISP) )

ISP bildirir ki, müştərilər istifadə etmədikləri interfeys üzvlərindən asılı olmağa məcbur edilməməlidir. Başqa sözlə, heç bir müştərini onlara aidiyyatı olmayan interfeys tətbiq etməyə məcbur etməyin.
ISP prinsipinə zidd nümunəyə baxaq:

<a href="https://im.ge/i/Fa6A5x"><img src="https://i.im.ge/2022/07/23/Fa6A5x.png" alt="Fa6A5x.png" border="0"></a>

<a href="https://im.ge/i/Fa6C8a"><img src="https://i.im.ge/2022/07/23/Fa6C8a.png" alt="Fa6C8a.png" border="0"></a>

Yuxarıdakı nümunədə Helikopter interfeysi və onun üç xüsusiyəti (`ucmaq()`,`pervane()`,`quyruq()`) verilmişdir.
Daha sonra Teyyare sinfi Helikopter interfeysindən miras almışdır. Baxdıqda rahatca görülür ki `pervane()` Helikopterə aid bir xüsusiyyət olduğu üçün gərəksiz bir şəkildə Teyyare sinfinə istifadəsi məcbur edilmişdir.


#### Aslılığın tərsinə çevrilməsi prinsipi (Dependency Inversion Principle (DIP) )

DIP bildirir ki, biz `siniflər` əvəzinə abstraksiyalardan (`interfeyslər` və `abstrakt siniflər`) asılı olmalıyıq. Abstraksiyalar detallardan asılı olmamalıdır; əvəzinə təfərrüatlar abstraksiyalardan asılı olmalıdır.
Gəlin bu prinsipə əks bir nümunəyə baxaq:

<a href="https://im.ge/i/FaNOkc"><img src="https://i.im.ge/2022/07/23/FaNOkc.png" alt="FaNOkc.png" border="0"></a>

<a href="https://im.ge/i/FaNX3r"><img src="https://i.im.ge/2022/07/23/FaNX3r.png" alt="FaNX3r.png" border="0"></a>

Yuxarıdakı nümunədə hələki heç bir problemin olduğu görünmür amma yeni bir izləmə platforması əlavə etdikdə Abunelik sinfində dəyişiklik edilmiş olacaq bu da Open-Close prinsipinin pozulmasına gətirib çıxaracaq. Burada `Abunelik()` sinfi bir növ `Netflix()` sinfindən asılı vəziyətdə qalır bunu aradan qaldırmaq üçün interfeyslərdən istifadə etməliyik:

<a href="https://im.ge/i/FaNsTa"><img src="https://i.im.ge/2022/07/23/FaNsTa.png" alt="FaNsTa.png" border="0"></a>

Bu dəfə asılılığı dəyişmək üçün `Platform()` interfeysi yaradıldı.

<a href="https://im.ge/i/FaN73y"><img src="https://i.im.ge/2022/07/23/FaN73y.png" alt="FaN73y.png" border="0"></a>

<a href="https://im.ge/i/FaNLqz"><img src="https://i.im.ge/2022/07/23/FaNLqz.png" alt="FaNLqz.png" border="0"></a>

Daha sonra sıra ilə `Netflix()` və `DisneyPlus()` sinifləri `Platform()` interfeysindən miras aldı.

<a href="https://im.ge/i/FaNUt6"><img src="https://i.im.ge/2022/07/23/FaNUt6.png" alt="FaNUt6.png" border="0"></a>

Nəhayət `Abunelik()` sinfi sadəcə `Platform()` interfeysini çağıraraq aslılığı aradan qaldırdı. Bu şəkildə olduqda yeni bir platformun əlavəsi heç bir kod dəyişikliyinə səbəb olmayacaq.

## İstinadlar

Bu yazı aşağıdaki mənbələrdən yararlanılaraq hazırlanmışdır:

- https://gokhana.medium.com/solid-nedir-solid-yaz%C4%B1l%C4%B1m-prensipleri-nelerdir-40fb9450408e
- https://www.educative.io/answers/what-are-the-solid-principles-in-java
- https://javatechonline.com/solid-principles-the-dependency-inversion-principle/
