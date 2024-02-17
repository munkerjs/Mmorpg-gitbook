---
description: >-
  Bu sayfa, oyunda kullanılan Blueprintler, Blueprint sonuçları, Blueprint
  reçeteleri ve Blueprint malzemeleriyle ilgili verileri depolamak için
  kullanılan yapıyı açıklar.
---

# 📘 Blueprints

Sayfa İçeriği

* [Blueprints](blueprints.md#blueprints)
* [BPRecipes](blueprints.md#bprecipes)
* [BPSupplies](blueprints.md#bpsupplies)
* [BluePrintResults](blueprints.md#blueprintresults)

### Blueprints

Blueprints tablosu, oyundaki Blueprintler hakkında bilgi depolar. Her Blueprintin bir adı, bir açıklaması ve bir BPResult kimliği vardır, BPResultId'leri aynı olamaz, her Blueprint'in benzersiz bir sonucu olmalıdır.

{% code lineNumbers="true" fullWidth="true" %}
```sql
[Name]                (nvarchar)           -> Blueprintin adı.
[Description]         (nvarchar)           -> Blueprintin açıklaması.
[BPResultId]          (int)                -> Blueprint Sonuçlarının tutulduğu tablonun ilişkisi
```
{% endcode %}

### BPRecipes

Blueprint Tariflerinin tablosu, Blueprint'leri tamamlamak için gereken malzemeleri ve miktarlarını listeler. Bir Blueprint Id'si, bir BlueprintSupply Id'si ve miktarı vardır.

{% code lineNumbers="true" fullWidth="true" %}
```sql
[BluePrintId]        (int)        -> Bağlı olduğu Blueprint'in ID'si
[BPSuppliesId]       (int)        -> Bağlı olduğu BPSupply'ın ID'si
[Amount]             (int)        -> Gerekli olan miktar
```
{% endcode %}

### BPSupplies

Blueprint tariflerinin gereken malzemelerini tutan tablodur. Tarifler için gerekli malzemeleri diğer tablolardan çağırmak için kullanılır.

{% code lineNumbers="true" fullWidth="true" %}
```sql
[SupplyType]        (int)        -> SupplyId'yi Doğru tabloda aratmak için, (1) Item (2) Material v.b.
[SupplyId]          (int)        -> Gerekli malzemenin Id`si
```
{% endcode %}

### BluePrintResults

Blueprint'lerin tamamlandığında vereceği sonuçları tutan tablodur.

{% code lineNumbers="true" fullWidth="true" %}
```sql
[ResultType]        (int)        -> ResultId'u doğru tabloda aratmak için, (1) Item, (2) Material v.b.
[ResultId]          (int)        -> Blueprint`in ürettiği malzemenin Id`si
```
{% endcode %}
