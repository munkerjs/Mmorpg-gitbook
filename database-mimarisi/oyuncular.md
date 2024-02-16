---
description: >-
  Oyun içerisindeki tüm kullanıcıların database mimarisi hakkında tüm bilgileri
  aşağıdan öğrenebilirsiniz.
---

# 🦸♂ Oyuncular

**Oyuncular Tablo Yapısı**&#x20;

* Users
* UserPremiumProducts&#x20;
* UserPremiumProducts\_Mapping

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

#### PremiumProducts **Tablosu**



#### UserPremiumProducts\_Mapping **Tablosu**

Premium üyelik alan üyelerin, paket bilgilerinin tutulduğu tablodur. Bu tabloda paketi / ürünü satın aldığı tarih ile bitiş tarihi bilgileri barınır. Ayrıca paket detayları için UserPremiumProducts tablosuyla ilişkiseldir.

<pre class="language-sql" data-title="UserPremiumProducts_Mapping " data-line-numbers data-full-width="true"><code class="lang-sql"><strong>      [UserId]            (int)       -> Users Tablosundaki Kullanıcı Id
</strong><strong>      [ProductId]         (int)       -> Premium Ürünler Tablosundaki Ürün Id
</strong>      [StartDate]         (datetime)  -> Premium Ürün Başlangıç Tarihi
      [LastDate]          (datetime)  -> Premium Ürün Bitiş Tarihi
</code></pre>

