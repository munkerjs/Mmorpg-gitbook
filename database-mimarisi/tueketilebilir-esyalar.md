---
description: >-
  Bu sayfa, oyunda kullanılan tüketilebilir ürünler, etkiler ve aralarındaki
  eşlemeyle ilgili verileri depolamak için kullanılan aşağıdaki tabloları
  açıklar:
---

# 🍹 Tüketilebilir Eşyalar

### &#x20;Consumable, Effect, ve ConsumableEffectMapper Tabloları

Sayfa İçeriği

* Tüketilebilir Ürünler
* Zamanlı Etkiler
* Etki Etkileri
* Tüketilebilir Ürün Etki Türleri
* Tüketilebilir Ürün Etki Eşleştirici

#### Consumables Tablosu

Tüketilebilir Ürünler tablosu, oyundaki tüketilebilir ürünler hakkında bilgi depolar. Her tüketilebilir ürünün benzersiz bir kimliği, bir adı, bir fiyatı ve oyuncular arasında takas edilip edilemeyeceğini gösteren bir Boole bayrağı vardır.

{% code lineNumbers="true" fullWidth="true" %}
```sql
[Name]        (nvarchar)        -> Consumable adı.
[Price]       (float)           -> Consumable oyun içi fiyatı.
[Tradeable]   (bit)             -> Oyuncular arasında takas edilip edilemeyeceğini
```
{% endcode %}

####

#### ConsumableEffectMapper Tablosu

Tüketilebilir Ürün Etki Eşleştirici tablosu, tüketilebilir ürünleri tüketilebilir ürün etki türlerine eşler. Tablodaki her girişin benzersiz bir kimliği, Consumables tablosuna referans veren bir yabancı anahtar ve ConsumableEffectTypes tablosuna referans veren bir yabancı anahtar vardır.

{% code lineNumbers="true" fullWidth="true" %}
```sql
[ConsumableId]    (int)        -> Consumables tablosuna referans veren bir anahtar.
[EffectTypeId]    (int)        -> ConsumableEffectTypes tablosuna referans veren bir anahtar.
```
{% endcode %}



**ConsumableEffectTypes Tablosu**

Etki Tipleri tablosu, bir tüketilebilir ürün tükettiklerinde oyunculara uygulanabilen etki tipleri hakkında bilgi depolar. Her etki etkisinin benzersiz bir kimliği ve bir tip kodu vardır.

{% code lineNumbers="true" fullWidth="true" %}
```sql
[EffectType]    (int)        -> Impact (Anında etkili), Timed (Süreli etkili)
[EffectId]      (int)        -> Gösterdiği efektin ID'si
```
{% endcode %}



**ConsumableImpactEffects Tablosu**

Tüketilebilir Etki Etkileri tablosu, oyuncular bir tüketilebilir ürün tükettiğinde onlara uygulanabilen etki etkileri hakkında bilgi depolar. Her etki etkisinin benzersiz bir kimliği ve bir tür kodu vardır.



{% code lineNumbers="true" fullWidth="true" %}
```sql
[Type]    (int)        -> Can verir, Mana verir v.b. (hasar arttırır v.b. özel durumlar)
[Value]   (float)      -> Verilecek etkinin değeri (500 Hasar arttır, 100 Can ver)
```
{% endcode %}



**ConsumableTimedEffects Tablosu**

Zamanlı Etkiler tablosu, bir tüketilebilir ürün tükettiklerinde oyunculara uygulanabilen zamanlı etkiler hakkında bilgi depolar. Her zamanlı etkinin benzersiz bir kimliği, bir tür kodu, bir değer ve saniye cinsinden bir süre vardır.

{% code lineNumbers="true" fullWidth="true" %}
```sql
[Type]        (int)        -> Can verir, Mana verir v.b. (hasar arttırır v.b. özel durumlar)
[Value]       (float)      -> Verilecek etkinin değeri (500 Hasar arttır, 100 Can ver)
[ForSeconds]  (float)      -> X süre boyunca etkili olacak
```
{% endcode %}

\
