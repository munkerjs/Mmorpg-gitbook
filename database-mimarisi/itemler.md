---
description: Oyun içerisindeki tüm eşya sisteminin database yapısıdır.
---

# ⚔ Itemler

Bu sayfa içerisinde MMORPG yaparken uygulanabilecek temel Tablo yapısı ve aralarındaki ilişkisel açıklamalar bulunmaktadır.&#x20;

#### Kullanılacak Frameworkler

* EntityFramework
* RabbitMQ

#### Itemler için Tablo Yapısı

* [Items](itemler.md#items-tablosu)
* [ItemTypes](itemler.md#itemtypes-tablosu)
* [ItemStats](itemler.md#itemstats-tablosu)
* [ItemSettings](itemler.md#itemsettings-tablosu)
* [ItemAdditionalInformations](itemler.md#itemadditionalinformations-tablosu)
* [Efsuns](itemler.md#efsuns-tablosu)
* [EfsunStats](itemler.md#efsunstats-tablosu)

#### Tabloların Anlamları ve Çalışma Mantıkları

#### **Items Tablosu**

Oyun içerisindeki tüm itemlerin barındığı genel tablodur. Bu tablo içerisinde oyunda hem Enemy hemde Klan üyelerinden düşecek tüm itemler mevcuttur. Eğer oyuna yeni bir item eklenecekse önce bu tabloya eklenmelidir.&#x20;

{% code title="Items" lineNumbers="true" fullWidth="true" %}
```sql
  [Name]             (nvarchar)   -> Item Adı
  [Rarity]           (int)        -> Item Değerliliği (Nadide, Şaheser, Efsanevi vs.)
  [ItemLevel]        (int)        -> Item ın Kullanılacağı Seviye
  [Gender]           (int)        -> (1)Erkek / (2)Kadın / (3)Tüm Cinsiyetler
  [isActivate]       (bit)        -> Item Oyunda Aktif mi Değil Mi?
  [CreatedAt]        (datetime)   -> Item Oluşturulma Tarihi
  [UpdatedAt]        (datetime)   -> Item Son Güncellenme Tarihi
  [TeamUserId]       (int)        -> Item Kim Tarafından Güncellenmiş?
  [Tradeable]        (bit)        -> Item Oyuncular Arasında Ticarete Açık mı?
  [Price]            (float)      -> NPC Satış Fiyatı
  [CharacterTypeId]  (int)        -> (1) Savaşçı, (2) Büyücü, (3) Şifacı
  [ItemStatsId]      (int)        -> Temel Item Özelliklerinin Tablo ID'si
  [ItemTypeId]       (int)        -> Item Türü (Zırh, Silah, Ceket, Pantolon vs.)
  [ItemSettingsId]   (int)        -> Envanter Ayarları
  [InformationsId]   (int)        -> Item Açıklaması - Bilgileri
  [EfsunId]          (int)        -> Item Özellikleri / Buff (Max Hasar, Can, vs.) 
```
{% endcode %}

#### ItemTypes Tablosu

Items tablosundaki ItemTypeId ile ilişkiseldir. Items tablosundaki Item nesnesinin genel niteliğini belirler. Buna örnek olarak aşağıdaki fotoğraflara bakabilirsiniz.

{% code title="ItemTypes " lineNumbers="true" fullWidth="true" %}
```
  [Name]            (nvarchar)    -> Item Türü (Zırh, Silah, Kolye, Yüzük, Ayakkabı vs.)
  [Types]           (nvarchar)    -> Item Tipi (Ağır, Hafif, Menzilli vs.)
```
{% endcode %}

<figure><img src="../.gitbook/assets/Ekran görüntüsü 2024-02-16 221303 (3).png" alt=""><figcaption><p>Items, ItemTypes ve ItemStats tablosu ile ilgilidir.</p></figcaption></figure>

#### ItemStats Tablosu

Items tablosundaki ItemStatsId ile ilişkiseldir. Items tablosundaki Item nesnesinin temel özelliklerini barındırır. Bu özellikler oyun içerisindeki her itemde olduğu gibi bazı itemlerde olmayadabilir. Bu nedenle veritabanı yapısına göre her zaman boş değerlerde (0) alabilir.

{% code title="ItemStats " lineNumbers="true" fullWidth="true" %}
```sql
  [Attack]            (float)    -> Item Nesnesinin Vuruş Hasarı
  [Defense]           (float)    -> Item Nesnesinin Savunma Miktarı
  [AttackSpeed]       (float)    -> ItemSaldırı Hızı 
  [CriticalHitPerc]   (float)    -> Item Nesnesinin Kritik Vurma İhtimali.
  [Durability]        (int)      -> Item Nesnesinin Eskime oranı.
```
{% endcode %}

#### ItemSettings Tablosu

Items tablosundaki ItemSettingsId ile ilişkiseldir. Item'ın envanter içerisindeki düzeni ile alakalı bilgilerin / ayarların barındığı tablodur. Her Item nesnesi için ayrı ayrı özellikler barındırır. Örneğin; envanterde 1 slotta kaç adet olacağı veya bölünebilir bir item olup olmadığının ayarı buradan yönetilir.

{% code title="ItemSettings " lineNumbers="true" fullWidth="true" %}
```sql
  [Unique]          (bit)        -> Aynı Anda Birden Fazla Kopyası Taşınamaz.
  [Stackable]       (bit)        -> Birden Fazla Kopyası Aynı Slota Taşınabilir.
```
{% endcode %}

#### **ItemAdditionalInformations Tablosu**

Items tablosundaki InformationsId değeri ile ilişkisel olup item hakkında açıklama, NPC bilgileri veya oyuncuya yönelik bilgilendirici mesajların detaylarını barındıran tablodur.&#x20;

{% code title="ItemAdditionalInformations " lineNumbers="true" fullWidth="true" %}
```sql
  [Description]       (nvarchar)    -> Item Açıklaması
  [Icon]              (nvarchar)    -> Item Resmi
  [SourceDescription] (nvarchar)    -> Itemin Nasıl Elde Edilebileceğinin Hakkında İpuçları
```
{% endcode %}

#### **Efsuns Tablosu**

Items tablosundaki EfsunId ile ilişkiseldir. Item nesnelerinin aldığı özelliklerin bulunduğu Mapping tablosudur diyebiliriz. Bu tablo içerisinde silaha atanan efsunun adı ve efsun grubunun Id değeri tutulur. Bu sayede bir iteme birden fazla efsun eklemesi yapılabilir. Oyuna yeni bir efsun eklenecekse bu tablodan eklenebilir. Fakat bu tablo düzgün kullanılmazsa oyunun dengesi değişebilir :)

{% code title="Efsuns " lineNumbers="true" fullWidth="true" %}
```sql
   [Name]              (nvarchar)    -> Efsun Adı
   [EfsunStatsId]      (int)         -> Efsun Grubu ID değeri      
```
{% endcode %}

#### **EfsunStats Tablosu**

Efsuns tablosundaki EfsunStatsId ile ilişkiseldir. Efsun grubu oluşturmanızı sağlar. Bu sayede bir item nesnesine atanan efsunlar ile oyun içerisindeki tüm dengeleri değiştirebilirsiniz :)

{% code title="EfsunStats " lineNumbers="true" fullWidth="true" %}
```
   [Value]              (float)    -> Örn: 5000 Can Veren bir itemse 5000 yapılır.
   [EnumType]           (int)      -> (0)Enemy, (1)Player (Kimi Öldürmek / Kurtarmak İçin Yaratılmışsa)
   [Description]        (text)     -> Yönetim Panelinde Efsunu Anlatan Açıklama
```
{% endcode %}

Efsun değerleri ile alakalı örneklere ulaşmak için;

1. [Savaşçı Efsun Örnekleri](https://istanbulkiyametvakti.fandom.com/tr/wiki/Sava%C5%9F%C3%A7%C4%B1\_-\_%C3%87emberlita%C5%9F\_E%C5%9Fyalar%C4%B1)
2. [Büyücü Efsun Örnekleri](https://istanbulkiyametvakti.fandom.com/tr/wiki/B%C3%BCy%C3%BCc%C3%BC\_-\_%C3%87emberlita%C5%9F\_E%C5%9Fyalar%C4%B1)
3. [Şifacı Efsun Örnekleri](https://istanbulkiyametvakti.fandom.com/tr/wiki/%C5%9Eifac%C4%B1\_-\_%C3%87emberlita%C5%9F\_E%C5%9Fyalar%C4%B1)

