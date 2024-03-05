# Temel Statlar

*Tüm sınıflar oyuna 95+5 stat puanı ile başlarlar, bu puanların 100 adet'i önceden belirlenmiş ve değiştirilemez minumum değerlerdir, sınıfı tanımlar ve sınıflar arası dengeyi oluşturmayı amaçlarlar.*

## Stat Bilgileri

- Maksimum stat puanı 99dur.
- Her 1 seviyede bir 3 stat puanı kazanır.
- Maksimum seviye 80 seviyedir
- Maksimum kazanılabilecek stat puanı 237 olacaktır.

* * *

- Strength (STR) => Bu, bir karakterin fiziksel gücünü belirler.
- Wisdom (WIS) => Bu, bir karakterin algısını ve içgörüsünü belirler.
- Dexterity (DEX) => Bu, bir karakterin çevikliğini belirler.
- Intelligence (INT) => Bu, bir karakterin hafızasını ve zihinsel keskinliğini belirler.
- Constitution (CON) => Bu, bir karakterin sağlığını ve dayanıklılığını belirler.
- Speciality (SPE) => Bu, bir karakterin sınıf gücünü belirler.

* * *

## Strength

> Yakın dövüş karakterlerini scale eden statdır, yakın dövüş karakterleri oyuna yüksek strength ile başlarlar. Strength yakın dövüş silahlarının düz vuruş hasarını arttırır.

* * *

## Wisdom

> Oyuncuların çevreden kazançlarını arttırır, gelen saldırılardan kaçınma ihtimali verir.

* * *

## Dexterity

> Uzak menzilli ve suikastçı sınıflarını scale eden statdır, uzak menzilli ve suikastçı karakterler oyuna yüksek miktarda dexterity ile başlarlar. uzun menzilli ve suikast saldırılarının hasarını arttırır.

* * *

## Intelligence

> Büyü kullanan karakterleri scale eden statdır, büyücü sınıflarını oyuna yüksek miktarda intelligence ile başlarlar. Intelligence büyülerin çarpanı olarak işlev görür.

* * *

## Constitution

> Tank karakterleri scale eden statdır, tank ve dayanıklı sınıflar oyuna yüksek miktarda constitution ile başlarlar, Karakterin canını arttırır. Gelen hasarları bloklama ihtimali verir.

* * *

## Speciality

> Tüm karakterler için ortak bir scale statdır, karakterlerin skillerinin hasarını arttırır. Tüm karakterler eşit speciality ile oyuna başlarlar.

* * *

  
<br/>

# Character Attributes

- Max Mana
- - Maximum manasını belirtir.
- Max Health
- - Maximum canını belirtir.
- Max Stamina
- - Maximum enerjisini belirtir.

* * *

- Mana Recovery
- - Saniye başına yenilediği manayı belirtir.
- Health Recovery
- - Saniye başına yenilediği canı belirtir.
- Stamina Recovery
- - Saniye başına yenilediği enerjiyi belirtir

* * *

- Spell Damage
- - Büyü ile vurulacak hasarı belirtir (büyü hasarı + spell damage)
- Spell Critical
- - Büyü ile kritik vurma ihtimalini belirtir.

* * *

- Physical Damage
- - Yakın dövüş hasarını belirtir (physical damage + silah hasarı)
- Physical  Critical
- - Yakın dövüş kritik ihtimalini belirtir.
- Armor
- - Fiziksel saldırlara direncini belirtir.

* * *

- Health Recovery IDLE
- Mana Recovery IDLE
- Stamina Recovery IDLE

> IDLE Dinlenirken yenilecek miktarlar.

* * *

- Frost Resitance
- - Buz direncini belirtir.
- Fire Resitance
- - Ateş direncini belirtir.
- Posion Resitance
- - Zehir direncini belirtir.
- Critical Resitance
- - Kritik direnci belirtir.
- Spell Resitance
- - Büyü direncini belirtir.

> Değerler 1000 Üzerinden hesaplanır, Resitance \* 0.1 ile yüzdesi hesaplanır.

* * *

- Dodge
- - Gelen hasarlardan kaçınma ihtimali (Wisdom \* 0.3)
- Block
- - Gelen hasarları engelleme ihtimali (Constitution \* 0.3)

> (%) Yüzdesel olarak hesaplanır.

* * *

# Örnek Sınıflar

## Barbar

### Temel Statlar

- Strength: 35
- Wisdom: 5
- Dexterity: 15
- Intelligence: 5
- Constitution: 25
- Speciality: 10

Dodge: 1.5% (Wisdom'e bağlı)  
Block: 9% (Constitution'a bağlı)

### Sınıf Bilgisi

- Barbar, yakın dövüşte üstün güç ve dayanıklılığa sahip bir savaşçıdır.
- Yüksek strength değeri, ona yakın dövüş silahlarıyla büyük hasar verebilme yeteneği verir.
- Yüksek constitution değeri sayesinde yüksek can ve hasar bloklama yeteneği vardır.

## Ranger

### Temel Statlar

- Strength: 10
- Wisdom: 20
- Dexterity: 30
- Intelligence: 10
- Constitution: 15
- Speciality: 10

Dodge: 6% (Wisdom'e bağlı)  
Block: 6% (Constitution'a bağlı)

### Sınıf Bilgisi

- Ranger, uzak menzilli savaşlarda ustalaşmış bir karakterdir.
- Yüksek wisdom değeri, çevresini daha iyi algılama ve saldırılardan kaçınma yeteneği sağlar.
- Yüksek dexterity değeri, ona uzun menzilli silahlarla yüksek hasar verebilme ve çevik hareket etme yeteneği kazandırır.

## Mage

### Temel Statlar

- Strength: 5
- Wisdom: 15
- Dexterity: 10
- Intelligence: 30
- Constitution: 15
- Speciality: 10

Dodge: 4.5% (Wisdom'e bağlı)  
Block: 4.5% (Constitution'a bağlı)

### Sınıf Bilgisi

- Mage, büyü kullanma konusunda uzmanlaşmış bir karakterdir.
- Yüksek intelligence değeri, büyülerin gücünü artırır ve ona daha etkili büyüler kullanma yeteneği verir.
- Orta düzeydeki wisdom değeri, saldırılardan kaçınma yeteneği sağlar.

## Paladin

### Temel Statlar

- Strength: 20
- Wisdom: 15
- Dexterity: 10
- Intelligence: 10
- Constitution: 30
- Speciality: 10

Dodge: 4.5% (Wisdom'e bağlı)  
Block: 9% (Constitution'a bağlı)

### Sınıf Bilgisi

- Paladin, hem savaşçı hem de destekleyici özelliklere sahip bir karakterdir.
- Yüksek strength ve constitution değerleri, hem güçlü saldırı hem de dayanıklılık sağlar.
- Orta düzeydeki wisdom değeri, çevresini algılama ve taktik kullanma yeteneği sağlar.

## Assassin

### Temel Statlar

- Strength: 10
- Wisdom: 20
- Dexterity: 30
- Intelligence: 10
- Constitution: 15
- Speciality: 10

Dodge: 6% (Wisdom'e bağlı)  
Block: 4.5% (Constitution'a bağlı)

### Sınıf Bilgisi

- Hızlı ve çevik hareket yeteneklerine sahiptir.
- Düşük dayanıklılığa rağmen, yüksek çeviklik ve reflekslerle saldırılardan kaçınabilir.
- Yüksek gözlem yeteneği sayesinde düşmanlarını şaşırtabilir ve hızlı, ölümcül saldırılar gerçekleştirebilir.
