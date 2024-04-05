---
title: Veeva Vault Integration Overview
description: Veeva Vault Integration Overview
exl-id: 52cc7290-b7e1-4476-877f-48934e6daf68
source-git-commit: 005c738818ab622a342ddc3a94e94638e344d058
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%

---

# Kom igång med Veeva Vault PromoMats och Adobe Experience Manager-integrering

Integreringen kommer att hantera ert innehåll, säkerställa rättigheter och regelefterlevnad och samtidigt utnyttja det ledande i leveransen av klassupplevelser.

För den här integreringen krävs minst följande programversioner:

* Adobe Experience Manager, 6.5.5+
* Veeva Vault PromoMats, 20R3.2+

>[!NOTE]
>
>Tjänstanvändare och lämpliga behörigheter krävs i båda systemen för integreringen.
>

>[!IMPORTANT]
>
>Den här funktionen är inte tillgänglig som en del av produkten. För genomförandet krävs underhållsavtal med Adobe Consulting. Kontakta din Adobe-representant om du vill veta mer.
>

## Principer och funktioner

Den här integreringen har stöd för två huvudsakliga användningsområden:

1. Innehållsgodkännande - När nytt innehåll har skapats eller befintligt innehåll har redigerats i AEM måste innehållet godkännas för användning i VPM som stöder godkännandeprocessen för medicin, juridik, regelefterlevnad (MLR) för biovetenskap.

2. Innehållshantering - Ge synlighet åt materialanvändningen genom att etablera relationer i PromoMats mellan digital taktik (t.ex. e-post, presentationer, webbplatser) och deras element (t.ex. logotyper, fotografi, grafik) som skapats i AEM för dokument med ursprung i AEM.

Fördelarna:

* Upprätthålla en enda källa till sanning för resurser och innehåll utan att behöva duplicera något digitalt arkiv.
* Utnyttja både Veeva Vault för hantering av rättigheter och efterlevnad och AEM för att skapa/leverera material och resurser i toppklass.
* Automatiserar rörligt innehåll och metadata mellan AEM och Veeva Vault.
* Minskar det manuella arbetet med att skicka innehåll till Veeva för arbetsflöden för godkännande.
* Varje system används för sina styrkor och kopplingen hjälper till att flytta innehåll automatiskt mellan systemen för att snabba upp time to market.

Vad gör integreringen?

* Stöder sändning AEM webbplatssidor, resurser, innehållsfragment och Experience Fragments till VPM. AEM sidor, innehållsfragment och Experience Fragments kan skickas som skärmdumpar i PDF eller bilder. AEM Assets binärfiler skickas i befintligt skick.
* Stöder manuell och automatiserad synkronisering av utvalda metadataelement som kan konfigureras från AEM till VPM.
* Stöder manuell och automatiserad synkronisering av utvalda metadataelement som kan konfigureras från VPM till AEM.
* Stöder relationer mellan AEM webbplatssidor, resurser, innehållsfragment och upplevelsefragment i VPM för att automatisera innehållsrelationer.
* Stöder återgivningsgenerering för flera enhetstyper.

>[!NOTE]
>
>Mer information om konfigurationsalternativ finns i dokumentationen om integreringsanvändning.
>

Vad gör INTE kontakten?

* Replikerar inte AEM processer och funktionalitet i Veeva eller vice versa.
* Gör inte MLR separat. Det hjälper till att automatisera överföringen av innehåll till Veeva där MLR förekommer.
* Ska inte användas för att skapa en identisk konfiguration mellan AEM och Veeva. Allt innehåll behöver inte flyttas mellan de två plattformarna.


>[!IMPORTANT]
>
>Den här integreringen ser för närvarande AEM som en källa till sanning för innehållssynkronisering.
>

## Hämta integreringen

För att kunna genomföra integreringen måste du följa stegen nedan.

Följ informationen i flödesschemat och flödesschemat nedan för att begära och konfigurera integreringen.

![Begär åtkomst](assets/integration-request.png)

Information om flödesschema (mappas till steg ovan):

* **Steg 1** - Du förutsätts redan ha eller håller på att köpa en licens för Veeva Vault PromoMats och för Adobe Experience Manager.
* **Steg 2** - En ny försäljningsorder som innehåller en beskrivning av ett underhållsavtal med Adobe Consulting måste undertecknas för att integreringen ska kunna utnyttjas.
* **Steg 3** - Installera, aktivera och konfigurera integreringspaketet.

## Support

Här beskrivs hur du kontaktar och loggar ett problem med supportteamet.

### Begär integrering eller Adobe Experience Manager support

Supportärenden kan loggas med Adobe kundtjänst. Din Adobe Experience Cloud-administratör måste logga in på [Adobe Admin Console](https://adminconsole.adobe.com/), klickar på fliken Support och skapar ett ärende. Om integreringsproblem uppstår måste du ta med följande information:

* **Processtitel**: `AEM - Veeva Vault Integration`
* **Processägare**: `Data Engineering`
* **Beskrivning**: `Description of the issue`
* **Kontaktpunkt**: `The email address(es) for relavant AEM point of contacts for your organization.`
* **AEM instans-URL**: `Place the Adobe Experience Manager instance url here.`
* **Veeva-instans-URL**: `Place the Veeva Vault PromoMats instance url here.`

### Begär Veeva Vault PromoMats Support

Ibland kan det problem som uppstår vara ett problem med funktionen för PromoMats-instansen Veeva Vault. I så fall kan din Veveva Vault PromoMats-administratör omdirigeras för att skapa en supportanmälan med [Veeva Support](http://support.veeva.com/). Du kan visa status för Veeva-instansen genom att navigera till [Veeva Trust](http://trust.veeva.com/).

