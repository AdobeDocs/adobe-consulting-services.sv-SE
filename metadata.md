---
product: adobe experience manager
solution: Experience Manager
description: Experience Manager dokumentation
type: Documentation
git-repo: https://github.com/AdobeDocs/adobe-consulting-services.sv-SE
index: y
source-git-commit: e2dac4b36fb94d72b72ef6f73a77e3f566539444
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---


# Metadata för intern användning

Metadata i GitHub-redigeringssystemet är hierarkiska och definieras enligt följande högre nivåer av prejudikat.

1. metadata.md
1. TillC
1. Artikel

Metadata som definieras i filen metadata.md gäller för hela repon, men kan åsidosättas på ToC- och artikelnivå. Alla åsidosättningar av metadata bör göras på lägsta möjliga nivå.

metadata.md

* `product`
* `git-repo`
* `index: y`

ToCS

* `sub-product`
* `user-guide-title`

Artikel

* `title`
* `description`

Mer information om metadata finns i [intern redigeringsguide](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/authoring/metadata.html).
