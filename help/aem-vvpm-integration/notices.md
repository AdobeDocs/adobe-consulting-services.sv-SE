---
title: Veeva Vault-integreringsmeddelanden
description: Veeva Vault-integreringsmeddelanden
exl-id: 1a188671-d123-4475-a607-65743ba0dadd
source-git-commit: 07eab1e439626bd3bb3416c9e7d0c1666927a7aa
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Bästa praxis, Guardrails och Notices

## Versioner

För den här integreringen krävs minst följande programversioner:

* Adobe Experience Manager, 6.5.5+
* Veeva Vault PromoMats, 20R3.2+

## Dataintegritet

Integrationen är utformad för att överföra innehåll mellan Adobe Experience Manager och Veeva Vault PromoMats. Som personuppgiftsansvarig ansvarar ditt företag för att följa alla lagar och regler för integritetsskydd som gäller för din insamling och användning av data.

## Synkroniseringsfrekvens för innehåll

AEM innehåll och metadata synkroniseras från AEM till VVPN när arbetsflödet för integrering har utlösts. Detta kan göras automatiskt eller manuellt. VPM-metadata synkroniseras från VPM till AEM. Detta kan du göra automatiskt med hjälp av en schemaläggare eller manuellt med ett knappklick.

## Begränsningar för integrering och bästa praxis och guardrutor

Tänk på följande begränsningar när du använder den här integreringen:

* Endast följande datatyper stöds vid synkronisering av metadata: &quot;Text&quot; och &quot;Flerradig text&quot;.
* Integreringen stöder AEM modulärt innehåll (innehållsfragment och upplevelsefragment) men inte VPM-modulärt innehåll.
* VPM-länkade dokument stöds inte.
* Synkronisering av visuella VPM-anteckningar från VVPM till AEM stöds inte.
* Integreringen importerar inte innehåll från VPM till AEM.
* Metadatavalidering stöds inte.
* Antalet dokument är begränsat baserat på Veeva-licensen. Se [Licensbegränsningar](#veeva-license-limitations).
* Antalet API-anrop är begränsat baserat på Veeva-licensen. Mer information finns i [API-begränsningar](https://developer.veevavault.com/docs/#what-are-rate-limits). Se [Licensbegränsningar](#veeva-license-limitations).

## Licensbegränsningar för Veeva

Du kan övervaka dina instansbegränsningar genom att gå till de allmänna VVPM-inställningarna.

![Veeva Limits](assets/veeva-limits.png)
