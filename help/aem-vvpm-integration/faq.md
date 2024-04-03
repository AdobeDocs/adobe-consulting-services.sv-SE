---
title: Vanliga frågor och svar om integrering av veeva Vault
description: Vanliga frågor och svar om integrering av veeva Vault
exl-id: c308ebb3-7881-4094-9f35-c67a96fb5ab1
source-git-commit: e4a5e55ac9b79a8de7dfa8ddd3d0ad99560917b8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Vanliga frågor

**Vilka metadata ska synkroniseras med Veeva?**

Det är viktigt att förstå metadata som baseras på innehållstypen (t.ex. kampanjer) i Veeva-portalen. När du har granskat vevevevektorportalen kan du skapa innehållsmetadatabilden i AEM för att lagra alla relevanta metadata för varje resurs/sida och konfigurera integreringen för att mappa metadata mellan de två systemen.

**Har integreringen stöd för Veeva-länkade dokument? Om inte, vilka relationstyper stöds?**

Nej. Se [Veeva-dokument](https://vaulthelp2.vod309.com/wordpress/admin-user-help/documents-admin-user-help/about-document-relationships/). Det länkade dokumentet (referensrelationstyp) är en av standardrelationstyperna som inte kan skapas eller tas bort via API eftersom de har ett särskilt vaultbeteende. Komponenter, stöddokument och andra som inte finns med i den här listan bör kunna konfigureras via AEM Veeva Cloud-konfiguration.

**Stöder integreringen det AEM modulära innehållet?**

Ja, integreringen stöder AEM innehållsfragment och Experience Fragments.

**Stöder integreringen det modulära innehållet Veeva?**

Nej, inte just nu.

**Synkroniserar integreringen Veeva visuella kommentarer med AEM?**

Nej, inte just nu. Visuella anteckningar är bara tillgängliga via API som PDF.

**Hur anger vi behörigheter för VPM-dokument som synkroniseras med integreringen?**

Integreringen använder en tjänstanvändare för att överföra dokument via API:t.  Standardregler och åsidosättningsregler för dokument (standardroller för dokument) stöds bara i VPM-användargränssnittet och inte när API:t används. Rekommendationen är att använda DAC (Dynamic Access Control) för rolltilldelningar. DAC används via alla kontaktpunkter, inklusive API:t. [Se dokumentationen här.](http://vaulthelp2.vod309.com/wordpress/admin-user-help/ah-user-permissions-access-control/about-dynamic-access-control-for-documents/)

**Stöder integreringen flera VVPM-instanser?**

Integreringen använder en molnkonfigurationsmetod som tillåter att flera veva-slutpunkter konfigureras från en AEM instans.

**Har integreringen stöd AEM publicering?**

Nej, den här integreringen fungerar bara med AEM författare. Det är avsett att underlätta granskningscyklerna för MLR innan innehållet publiceras.
