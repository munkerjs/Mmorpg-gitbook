---
description: Giriş
---

# 😇 Database Mimarisi

Bu sayfa içerisinde MMORPG yaparken uygulanabilecek temel Tablo yapısı ve aralarındaki ilişkisel açıklamalar bulunmaktadır.&#x20;

#### Kullanılacak Frameworkler

* EntityFramework

#### Itemler için Tablo Yapısı

* Items
* ItemStats
* ItemTypes
* ItemProperties
* ItemAdditionalInformations
* Efsuns
* EfsunStats

#### Tabloların Anlamları ve Çalışma Mantıkları

**Items Tablosu**

Oyun içerisindeki tüm itemlerin barındığı genel tablodur. Bu tablo içerisinde oyunda hem Enemy hemde Klan üyelerinden düşecek tüm itemler mevcuttur. Eğer oyuna yeni bir item eklenecekse önce bu tabloya eklenmelidir.&#x20;

{% code lineNumbers="true" fullWidth="true" %}
```sql
  [Name]             (nvarchar)   -> Item Adı
  [Rarity]           (int)        -> Item Değerliliği (Nadide, Şaheser, Efsanevi vs.)
  [ItemLevel]        (int)        -> Item ın Kullanılacağı Seviye
  [Gender]           (int)        -> (1)Erkek / (2)Kadın / (3)Tüm Cinsiyetler
  [isActivate]       (bit)        -> Item oyunda aktif mi değil mi?
  [Tradeable]        (bit)        -> Item Oyuncular Arasında Ticarete Açık mı?
  [Price]            (float)      -> NPC Satış Fiyatı
  [CharacterTypeId]  (int)        -> (1) Savaşçı, (2) Büyücü, (3) Şifacı
  [ItemStatsId]      (int)        -> Temel Item Özelliklerinin Tablo ID'si
  [ItemTypeId]       (int)        -> Item Türü (Zırh, Silah, Ceket, Pantolon vs.)
  [ItemPropertiesId] (int)        -> Envanter Ayarları
  [InformationsId]   (int)        -> Item Açıklaması - Bilgileri
  [EfsunId]          (int)        -> Item Özellikleri / Buff (Max Hasar, Can, vs.) 
```
{% endcode %}

#### ItemTypes Tablosu

Items tablosundaki ItemTypeId ile ilişkiseldir. Items tablosundaki Item nesnesinin genel niteliğini belirler. Buna örnek olarak aşağıdaki fotoğraflara bakabilirsiniz.

{% code lineNumbers="true" fullWidth="true" %}
```
  [Name]            (nvarchar)    -> Item Türü (Zırh, Silah, Kolye, Yüzük, Ayakkabı vs.)
  [Types]           (nvarchar)    -> Item Tipi (Ağır, Hafif, Menzilli vs.)
```
{% endcode %}

<figure><img src=".gitbook/assets/Ekran görüntüsü 2024-02-16 221303 (3).png" alt=""><figcaption><p>Items, ItemTypes ve ItemStats tablosu ile ilgilidir.</p></figcaption></figure>

#### ItemStats Tablosu

Items tablosundaki ItemStatsId ile ilişkiseldir. Items tablosundaki Item nesnesinin temel özelliklerini barındırır. Bu özellikler oyun içerisindeki her itemde olduğu gibi bazı itemlerde olmayadabilir. Bu nedenle veritabanı yapısına göre her zaman boş değerlerde (0) alabilir.

{% code lineNumbers="true" fullWidth="true" %}
```sql
  [Attack]            (float)    -> Item Nesnesinin Vuruş Hasarı
  [Defense]           (float)    -> Item Nesnesinin Savunma Miktarı
  [AttackSpeed]       (float)    -> ItemSaldırı Hızı 
  [CriticalHitPerc]   (float)    -> Item Nesnesinin Kritik Vurma İhtimali.
  [Durability]        (int)      -> Item Nesnesinin Eskime oranı.
```
{% endcode %}

