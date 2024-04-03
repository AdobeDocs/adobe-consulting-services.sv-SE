---
source-git-commit: bdc8e76125282ab294e34c5216311524e015c175
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 4%

---
# Riktlinjer för att bidra till Adobe konsulttjänster

## Dokumentationsfilosofi

Vi vet att Adobe Experience Manager-användare arbetar i mycket konkurrensutsatta miljöer och strävar efter att skapa digitala upplevelser som skiljer dem från deras konkurrenter. Därför är det viktigt att ACS, när ACS levererar avancerade nya verktyg för AEM, kompletterar dessa verktyg med korrekt och tydlig dokumentation så att kunden omedelbart kan utnyttja sin AEM och maximera avkastningen.

Målet med ACS-dokumentationen är att ge AEM tillgång till dokumentation så snart som möjligt. Därför prioriterar vi korrekt, användbar dokumentation och strävar efter att kontinuerligt uppdatera och förbättra den.

## Dokumentationsbidrag

I syfte att kontinuerligt förbättra ACS-dokumentationen är det välkommet för AEM användare att bidra till dokumentationen. Vare sig det gäller förfrågningar eller frågor kan förbättringar av dokumentationen vara korrigeringar, förtydliganden, tillägg och ytterligare exempel.

## Dokumentationsstandarder

Vi välkomnar bidrag till vår dokumentation, men alla bidrag till AEM, antingen i form av en begäran om att tjänsten ska kunna hämtas eller ett problem, bör överensstämma med våra standarder för bidrag och dokumentation.

Bidrag som inte uppfyller dessa standarder kan avvisas.

### Vi dokumenterar standardanvändningsexempel.

ACS-dokumentationen omfattar standardanvändningsfall. Användningsfall som inte omfattas av standardinstallation och -användning av produkten ingår inte i ACS-dokumentationen.

### Vi dokumenterar vanligtvis inte buggar eller deras tillfälliga lösningar.

ACS-dokumentationen omfattar standardanvändningsfall. Av den anledningen är buggar, effekter orsakade av buggar och tillfälliga lösningar för buggar i allmänhet inte dokumenterade.

Undantag från den här regeln gäller versionsinformationen där kända problem kan listas med möjliga lösningar som har godkänts av AEM produkthantering.

### Dokumentationsbidragen är inte till för att besvara tekniska frågor.

Alla idéer du kan behöva för att förbättra ACS-dokumentationen är välkomna som bidrag. Kommentarer, problem och förfrågningar är dock avsedda för *avgifter* endast. De är inte avsedda att användas för att besvara frågor om hur du använder AEM, implementerar ditt AEM eller löser tekniska problem.

Om du har frågor om hur AEM eller tekniska fel har använts ska du rapportera via den normala supportprocessen via [Experience Cloud Enterprise Support Portal](https://helpx.adobe.com/se/contact/enterprise-support.ec.html) eller diskuteras i [Experience Manager community](https://forums.adobe.com/community/experience-cloud/marketing-cloud/experience-manager).

***ACS-dokumentationsavgifter ersätter inte Adobe kundtjänst*** och eventuella bidrag som söker svar på frågor som rör stöd kommer att refuseras.

### Bidragen ska tydligt hänvisa till berörda dokumentationssidor.

Om du skapar ett problem som kan föreslå förbättringar av dokumentationen måste du inkludera länkar till de sidor som påverkas. Om du skapar ett ärende genom att använda länken **Redigera den här sidan** på en dokumentationssida skapas ärendet automatiskt med en länk till sidan.

Detta gäller inte för pull-begäranden eftersom pull-begäranden till sin natur refererar till den eller de berörda sidorna.

## Riktlinjer för dokumentation

Vi ber att eventuella bidrag till vår dokumentation följer vissa riktlinjer för format.

Genom att följa dessa riktlinjer blir det enklare att granska ditt bidrag och det går därför snabbare att integrera det i vår dokumentation.

### Språk och format

#### Språk

* ACS-dokumentationen skrivs och underhålls på amerikansk engelska.
* Håll meningar så enkla som möjligt.
* Se till att språket är klart och koncist.

Kom ihåg att läsare av ACS-dokumentation finns i hela världen och inte kan förväntas vara inbyggda eller flytande engelska högtalare. Undvik kollokvialism och håll språket så tydligt och enkelt som möjligt.

#### Följ Microsoft formathandbok

[The Microsoft Manual of Style](https://docs.microsoft.com/en-us/style-guide/welcome/) är en kostnadsfri handbok för dokumentationsformat som fokuserar på programvarudokumentation och AEM dokumentation följer den här handboken när det är möjligt.

### Formatering

| Objekt | Stil |
|---|---|
| Element eller alternativ i användargränssnittet | **fet** |
| Filnamn, sökväg, användarindata, parametervärden | `monospaced` |
| Kod, kommandorad | ```Code Block``` |

### Skärmbilder

Skärmbilder ska användas med omdöme och endast när en textbeskrivning är otillräcklig.

Markörer eller andra anteckningar i skärmbilder (som röda ramar, pilar eller text) bör inte användas. På så sätt är skärmbilderna enklare att återanvända eller att replikera i lokaliserade versioner av dokumentationen.

### Versionsspecifika referenser

Undvik om möjligt direkta referenser till en viss version i dokumentationsinnehållet. Detta gör dokumentationen mer flexibel och utbyggbar för framtida versioner.

### Användning av dag, AEM, CQ, CRX

Produktens fullständiga namn ska alltid anges **Adobe Experience Manager** för första gången i en artikel och kan därefter kallas **AEM**.

Day, Day Software, CQ och CRX bör inte användas utom när det är oundvikligt, t.ex. i klassnamn eller med hänvisning till AEM.