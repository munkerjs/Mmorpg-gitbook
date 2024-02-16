---
description: >-
  Oyun içerisindeki tüm kullanıcıların database mimarisi hakkında tüm bilgileri
  aşağıdan öğrenebilirsiniz.
---

# 🦸♂ Oyuncular

**Oyuncular Tablo Yapısı**&#x20;

* Users
* PremiumProducts
* UserPremiumProducts\_Mapping

***

#### Tabloların Anlamları ve Çalışma Mantıkları

#### **Users Tablosu**

Oyuna kayıtlı oyuncuların temel oturum bilgilerinin barındığı ana tablodur.

{% code title="Users" overflow="wrap" lineNumbers="true" fullWidth="true" %}
```sql
      [Email]               (nvarchar)       -> Oyuna Giriş Bilgisi
      [Password]            (nvarchar)       -> Oyuna Giriş Bilgisi
      [Username]            (nvarchar)       -> Oyuna Giriş Bilgisi
      [PhoneNumber]         (nvarchar)       -> İletişim Bilgisi
      [BirthDay]            (datetime)       -> Dogum Tarihi, Boş Olabilir
      [IpAdress]            (nvarchar)       -> Kayıt Olduğundaki IP Adresi
      [IsActive]            (int)            -> (0)Pasif, (1)Aktif, (2)VAC Ban
      [PremiumTypeId]       (int)            -> Ayrıcalıklı Paket Alan Oyuncuların Mapping ID Değeri
      [CreatedAt]           (CreatedAt)      -> Kayıt Tarihi    
      [UpdatedAt]           (CreatedAt)      -> Güncellenme Tarihi  
```
{% endcode %}

**Parametre Notları / Açıklamaları**

**Password:** MD5 ve Sha256 ile şifrelenmiş şekilde tutulmaktadır. Ayrıca bir SALT ile şifrelenmesi gerekmektedir. SALT değeri projeden bağımsız bir depoda saklanacaktır.\
**BirthDay:** Doğum günü bilgisi ile doğum gününe özel hediye materyal, item verilebilir. \
**PremiumTypeId**: Oyuncu, para ile bir ayrıcalıklı paket almışsa bu alan tutulmaktadır. Eğer değeri 0 ise standart ücretsiz oyuncudur.

***

#### PremiumProducts **Tablosu**

Her oyunun bir yerden para kazanması gerekmektedir. Bu tabloda ise oyunculara premium eşyalar / nitelikler satabiliriz. Fakat buna örnek olarak aylık premium üyelik, maden arttıcı gibi özellikleri gösterebiliriz. Hiç bir zaman pay to win olmayacaktır.

<pre class="language-sql" data-title="PremiumProducts " data-line-numbers data-full-width="true"><code class="lang-sql"><strong>      [Name]              (nvarchar)    -> Paket Adı (Örn: Plus Paket)
</strong><strong>      [Description]       (nvarchar)    -> Paket Açıklaması
</strong><strong>      [Price]             (float)       -> Satış Fiyatı (Akçe, Sikke vs.)
</strong>      [CategoryId]        (int)         -> Paket Kategorisi (Yardımcı, Silahlar, Paketler vs.)
      [EfsunId]           (int)         -> Paket Özellikleri 
      [MaxDay]            (int)         -> Paketin Geçerlilik Süresi (0 Gün, 30 Gün, 7 Gün vs.)
</code></pre>

**Parametre Notları / Açıklamaları**

**MaxDay**: Bu değer 0 ise, paket sınırsız olarak kullanılır. \
**EfsunId**: Bu değer ile oyun içerisinde etki edecek özelliklerin grubunu belirtmekteyiz. \
**CategoryId**: Bu değer ile marketplace yapıldığında ürünleri kategorize etmek için kullanacağız.\
**Price**: E-Pin kodları ile elde edilecek oyun parasıyla buradaki **price** değerine göre ürünler marketplace de satın alınabilecek.

***

#### UserPremiumProducts\_Mapping **Tablosu**

Premium üyelik alan üyelerin, paket bilgilerinin tutulduğu tablodur. Bu tabloda paketi / ürünü satın aldığı tarih ile bitiş tarihi bilgileri barınır. Ayrıca paket detayları için UserPremiumProducts tablosuyla ilişkiseldir.

<pre class="language-sql" data-title="UserPremiumProducts_Mapping " data-line-numbers data-full-width="true"><code class="lang-sql"><strong>      [UserId]            (int)       -> Users Tablosundaki Kullanıcı Id
</strong><strong>      [ProductId]         (int)       -> Premium Ürünler Tablosundaki Ürün Id
</strong>      [StartDate]         (datetime)  -> Premium Ürün Başlangıç Tarihi
      [LastDate]          (datetime)  -> Premium Ürün Bitiş Tarihi
</code></pre>

***

Devam Edilecektir..
