+++
title = "racket dasturlash tili"
date = "2024-06-17"
description = "racket dasturlash tiliga amaliy qo'llanma."
taxonomies.tags = [
    "racket",
    "dasturlash",
    "boshlang'ich",
]
+++

racket
---

[racket](https://racket-lang.org) mening eng sevimli dasturlash tilim. lekin siz uni men yoqtirgan til bo'lgani uchun emas, balki u ifodaviy qudrati juda ham kuchli bo'lgani uchun o'rganishingiz kerak. agarda sizda boshqa zamonaviy, keng tarqalgan go, python, java yoki rust kabi dasturlash tillari bilan yetarlicha qiyinlikdagi loyihalar ustida ishlash tajribangiz bo'lsa, racket ning o'sha ifodaviy qudratini boshqalardanda ko'proq ko'ra olasiz. agarda siz dasturlashga endigina kirib kelayotgan bo'lsangiz ham, hech cho'chimang, chunki siz ishonchli qo'llardasiz. racket mening kamtargina fikrimga ko'ra, boshlang'ich o'quvchilar uchun eng mukammal dasturlash tili. ishonaveringki faqatgina men bu fikrda emasman: dasturlash sohasida mendan juda ham ko'p tajribaga ega va racket ni nafaqat boshlang'ich o'quvchilar uchun, hattoki mutaxasis dasturchilar uchun ham eng mukammal dasturlash tili deb hisoblaydigan bir qancha insonlarni bilaman. shunday qilib racket ni o'rganishda qiziqarli vaqt o'tkazasiz degan umiddaman :)

o'zingizga savol bering
---

eng birinchi navbatda o'zingizdan "til nima vazifani bajaradi?" degan savolni so'rashingizni va u haqida biroz muddat bosh qotirishingizni xoxlayman.

til bu shunchaki vositachi mexanizm. nega mushukni aynan mushuk, balki kuchuk emas deb atashimizda aslida hech qanday ma'no yo'q. bu shunchaki jamiatimiz birgalikda qabul qilgan so'z. asl mohiyat esa mushuk so'zini eshitganimizda ko'z oldimizga keladigan to'rt oyoqli jonivordir. nega 1 ni aynan 1 kabi yozamiz ? bu ham shunchaki ko'pchilik tomonidan qabul qilingan g'oya xolos. asl mohiyat esa 1 ni ko'rganimizda ongimizga keladigan yagonalik tushunchasida. demak til bu ma'noni tashiydigan (bir agentdan ikkinchi agentga olib boradigan) vositachidir. dasturlash tili ham bundan istisno emas. dasturlash tili ham shunchaki bir vositachi xolos. allaqachon siz "yaxshi, lekin nima bilan nima ning o'rtasidagi vositachi?" degan savolni berishga ulgurgan bo'lsangiz kerak. biz o'zaro mulaqot qilishda ishlatadigan tabiiy tillar ikki yoki undan ortiq odamlar o'rtasidagi vositachi bo'lsa, dasturlash tillari esa kampyuterimiz va bizning o'rtamizdagi vositachilardir. qizig'i shundaki biz kampyuterlarimizning tilini, kampyuterlarimiz esa bizning tilimizni to'g'ridan to'g'ri tushunishmaydi. bunda dasturlash tili biz yozgan (odam tiliga yaqin ko'rinishdagi) ifodalarni kampyuter bir qancha turli xil jarayonlardan o'tkazib ishlata olishi uchun kampyuter tushunadigan ifodalarga o'girib beradi.

kerakli dasturlarni o'rnatish
---

demak biz kampyuterimiz bilan racket orqali gapirmoqchi bo'lsak, birinchi navbatda o'sha "tarjimon" vositachini kampyuterimizga o'rnatib olishimi kerak bo'ladi. buning uchun racket ning [racket-lang.org](https://racket-lang.org) rasmiy vebsaytiga tashrif buyurib, so'ngra "download" qismiga o'ting va o'zingizning platformangizga mos dasturni yuklab oling.

![racket-logo](https://download.racket-lang.org/logo-and-text-1-2.png)

agarda siz bu dasturni muvaffaqiyatli tarzda o'rnatgan bo'lsangiz, u sizning qurilmangizda (kampyuteringizda) 3 ta juda eng asosiy dasturlarni o'rnatadi:

* racket, bu biz aytib o'tgan "tarjimon" ning xuddi o'zi. dasturlash tilida uni interpreter yoki compiler deb atashingiz mumkin. interpreter (tarjimon) va compiler (yig'uvchi) o'rtasida juda muhim farqlar bor, lekin hozirlikcha siz ularni bir xil deb o'ylasangiz ham hech qanday qo'pol xatolikga yo'l qo'ymagan bo'lasiz.

* drracket, bu racket dasturlash tilida kod (dastur) yozishimiz uchun kerak bo'ladigan tahrirchi, grafik dasturdir. drracket racket dasturlash tilida kod yozish uchun 100% zarur bo'lgan dastur emas, u shunchaki bizning kunimizni oson qiladi xolos. faktlarga asoslanib gapiradigan bo'lsak ham, siz drracket ni ishlatmasdan turib ham bemalol kod (dastur) yoza olasiz.

* raco, bu racket kodlarni (ingliz tilida "source code") haqiqiy dasturga (ingliz tilida "executable" yoki ba'zan "binary") o'girish, yozayotgan kodimizga boshqa dasturchilar tomonidan yozilgan qo'shimcha kutubxonalarni (ingliz tilida "library") olib kelish va shunga o'xshah muhim vazifalarni bajarish uchun ishlatiladigan dasturdir.