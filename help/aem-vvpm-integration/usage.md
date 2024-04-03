---
title: Integreringsanvändning för Veeva Vault
description: Integreringsanvändning för Veeva Vault
exl-id: efff7af1-eb25-4a1d-b7ef-52e3336970ff
source-git-commit: 19949a48cfee0c17481e52f286a460e9d81d7ff0
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---

# Integreringsanvändning

## Genomgång

I följande videogenomgång beskrivs hur du använder kontakten:

>[!VIDEO](https://video.tv.adobe.com/v/332137/?quality=12&learn=on)

## Inställningar

Den här guiden hjälper dig att få igång kontakten.

>[!IMPORTANT]
>
>För varje system måste dessa steg utföras av en **administratör** för varje system.
>
>Steg i den här dokumentationen hjälper dig att skapa integreringar/registreringar som inbegriper tilldelning av behörigheter och/eller administratörsåtkomst.  Det är ditt ansvar att se till att dessa steg följer företagets regler innan de utförs och att de utförs med omsorg.
>

### Installera integreringspaket

Du får åtkomst till AEM. Det finns två alternativ för att installera integrationen:

1. **Paketinstallation** - Direkt framåt och mindre involverat.
2. **POM-installation** - Mer avancerat, men kan vara användbart när du använder AEM Cloud Manager och uppgraderar integreringen.

#### Paketinstallation

Om du vill installera paketet hämtar du det med länken i e-postmeddelandet om introduktion. [Klicka här om du vill ha mer information om hur du installerar ett AEM.](https://experienceleague.adobe.com/docs/experience-manager-64/administering/contentmanagement/package-manager.html?#installing-packages)

#### POM-installation

Följ de här stegen för att inkludera kopplingen i din POM. Ersätt ditt användarnamn och lösenord med de som finns i e-postmeddelandet om introduktion.

1. Lägg till följande i `.cloudmanager/maven/settings.xml` i ditt projekt eller `~/.m2/settings.xml` på datorn. Ersätt `YOUR_USERNAME` med användarnamnet och `YOUR_PASSWORD` med det lösenord som anges i e-postmeddelandet om introduktion.

   >[!IMPORTANT]
   >
   >Om du använder molnhanteraren är den säkra metoden att följa de steg som beskrivs här för [lösenordsskyddade Maven-databaser](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/create-application-project/setting-up-project.html?lang=en#password-protected-maven-repositories).
   >

   ```
   <settings>
       ...
       <servers>
           ...
           <server>
               <id>repo.ea.adobe.net</id>
               <username>YOUR_USERNAME</username>
               <password>YOUR_PASSWORD</password>
               <filePermissions>BucketOwnerFullControl</filePermissions>
               <configuration>
                 <wagonProvider>s3</wagonProvider>
               </configuration>
           </server>
           ...
       </servers>
       ...
   </settings>
   ```

2. Lägg till följande i projektets `pom.xml` fil:

   ```
   <project>
       ...
       <build>
           ...
           <extensions>
               ...
               <extension>
                   <groupId>com.allogy.maven.wagon</groupId>
                   <artifactId>maven-s3-wagon</artifactId>
                   <version>1.2.0</version>
               </extension>
               ...
           </extensions>
           ...
       </build>
       ...
       <repositories>
           ...
           <repository>
               <id>repo.ea.adobe.net</id>
               <url>s3://repo.ea.adobe.net/release</url>
               <releases>
                   <enabled>true</enabled>
               </releases>
           </repository>
           ...
       </repositories>
       ...
   </project>
   ```

3. Lägg till följande i projektets `all/pom.xml` -fil. Ersätt `project.dependencies.dependency.version` med lämplig version och `project.build.plugins.plugin.configuration.embeddeds.embedded.target` med rätt sökväg.

   ```
   <project>
       ...
       <build>
           ...
           <plugins>
               ...
               <plugin>
                   <groupId>org.apache.jackrabbit</groupId>
                   <artifactId>filevault-package-maven-plugin</artifactId>
                   ...
                   <configuration>
                       ...
                       <embeddeds>
                           ...
                           <embedded>
                               <groupId>com.adobe.acs.aemveeva</groupId>
                               <artifactId>aem-veeva-connector.all</artifactId>
                               <type>zip</type>
                               <target>/apps/APP_NAME-packages/application/install</target>
                           </embedded>
                           ...
                       </embeddeds>
                   </configuration>
               </plugin>
               ...
           </plugins>
           ...
       </build>
       ...
       <dependencies>
           ...
           <dependency>
               <groupId>com.adobe.acs.aemveeva</groupId>
               <artifactId>aem-veeva-connector.all</artifactId>
               <version>1.0.5</version>
               <type>zip</type>
           </dependency>            
           ...
       </dependencies>
       ...
   </project>
   ```

### Molnkonfiguration

Den här integreringen konfigureras genom att en molnkonfiguration skapas i den mapp som anslutningen ska arbeta i. Så här skapar du en molnkonfiguration:

1. Navigera till veeva molnkonfiguration.

   ![Navigera till molnkonfiguration](assets/cloud-config-navigate.png)

2. Skapa en ny veeva-molnkonfiguration i rätt mapp och fyll i enligt anvisningarna i nästa avsnitt.

   ![Skapa molnkonfiguration](assets/cloud-config-create.png)

#### Fliken Konfiguration

Fyll i följande på konfigurationsfliken:

![Fliken Konfiguration](assets/configuration-tab.png)

1. Obligatoriskt. Title for Veeva Vault connector configuration. Detta kan vara ett godtyckligt värde. (till exempel `Veeva Vault Configuration`)
2. Obligatoriskt. Veeva-instansens domänadress (t.ex. `https://my-instance.veevavault.com/`)
3. Obligatoriskt. ClientID krävs för att anropa Vevaevavans API. Detta kan vara ett godtyckligt värde och används oftast för felsökning. (till exempel `adobe-aem-vvtechpartner`)
4. Obligatoriskt. Veeva Vault-användarnamn. Se [Veeva - Skapa användare](#veeva-user-creation).
5. Obligatoriskt. Veeva Vault-lösenord. Se [Veeva - Skapa användare](#veeva-user-creation).

#### Adobe IO-flik

Om projektet behöver generera PDF eller bilder för sidor är den här fliken obligatorisk. Fyll i följande på fliken adobe io:

![Adobe IO-flik](assets/adobe-io-tab.png)

1. Obligatoriskt. Adobe IO-slutpunkten för att skapa PDF-bilder som fanns i e-postmeddelandet om introduktion. (till exempel `https://my-namespace.adobeioruntime.net/api/v1/web/aem-veeva-serverless-0.0.2/trigger-action.json`)
2. Obligatoriskt. Åtgärdsnamnet för generering av sidbilder. Värdet måste vara `aem-veeva-integration/get-image-async`.
3. Obligatoriskt. Åtgärdsnamn för generering av HTML-bilder. Värdet måste vara `aem-veeva-integration/get-pdf-async-new`.
4. Obligatoriskt. Adobe IO-slutpunkten för att få status för den generation som angavs i e-postmeddelandet om introduktion.(till exempel `https://my-namespace.adobeioruntime.net/api/v1/web/aem-veeva-serverless-0.0.2/get-state-value`)
5. Obligatoriskt. AEM användarnamn som ska användas av Adobe IO. Se [Skapa AEM](#aem-user-creation).
6. Obligatoriskt. AEM lösenord som ska användas av Adobe IO. Se [Skapa AEM](#aem-user-creation).
7. Valfritt. Standardtimeout är att låta sidan svara tills en viss tid efter vilken AIO-tjänsten slutar försöka få ett svar. Standardvärdet är `30000`.
8. Valfritt. Fördröjning är efter att sidan har svarat med 200 för att fördröja återgivningen av alla bilder innan skärmbilden tas. Standardvärdet är `2000`.
9. Valfritt. Den URL som genereras av skärmbild/PDF upphör att gälla om ett konfigurerat värde anges i sekunder.
10. Valfritt. Adobe IO-skärmbild/PDF-genereringstjänsten är asynkron. AEM anropar AIO-statusslutpunkten för att hämta skärmbild/PDF. Den här egenskapen avgör i millisekunder pausen mellan i varje statusanrop. Standardvärdet är `10000`.
11. Valfritt. Maximalt antal nya försök för statusanrop till Adobe IO för att hämta skärmbild/PDF. Standardvärdet är `10`.

#### Avancerad flik

Fyll i följande på fliken Avancerat:

![Avancerad flik](assets/advanced-tab.png)

1. Krävs för PDF/bildgenerering. Filnamnsmönstret som används när PDF/bilder skapas. `{name}` kan mallas. (till exempel `{name}-screenshot`)
2. Valfritt. De enhetstyper för vilka sidskärmbilder krävs, förutom Skrivbord. Giltiga typer är `Tab (iPad)`och `Mobile (iPhone X)`.
3. Valfritt. Återgivningstypsvärdet i Veeva som representerar återgivningen ovan. (till exempel `web_ready__c`)
4. Krävs för PDF/bildgenerering. Skärmbildstyp att skapa. Antingen `PDF` eller `Image`.
5. Krävs för PDF/bildgenerering. Den PDF-typ som ska genereras. Antingen `Print CSS Based PDF` eller `Pixel Perfect Screenshot PDF`.
6. Krävs för PDF/bildgenerering. Den bildtyp som ska genereras. Antingen `PNG` eller `JPEG`.
7. Obligatoriskt. Arbetsflöde som ska köras när Veeva Vault Approval-utlösaren är klar.
8. Obligatoriskt. Status-egenskapsvärde som representerar Godkänd. (till exempel `Approved for Distribution`)
9. Obligatoriskt. Arbetsflöde som körs när veeva Vault Reject-utlösaren är klar.
10. Obligatoriskt. Status-egenskapsvärde som representerar Avvisat/ej godkänt. (till exempel `Rejected`)
11. Valfritt. Egenskapsnamn för dokument-ID i veeva Vault. Standardvärdet är `id`.
12. Valfritt. Egenskapsnamn för status i veeva Vault. Standardvärdet är `status__v`.
13. Valfritt. Egenskapsnamn för dokumentets ändringsdatum. Standardvärdet är `version_modified_date__v`.
14. Valfritt. Egenskapsnamn för dokumentresurs-URL. Standardvärdet kommer att `external_id__v`. Om fältet redan används skapar du ett annat fält i Veeva och fyller i fältnamnet här. Det här fältet kommer att användas i Veeva för AEM resurssökväg. Detta krävs för automatisk synkronisering av metadata.
15. Valfritt. Egenskapsnamn för huvudversionsnummer i Veeva Vault. Standardvärdet är `major_version_number__v`.
16. Valfritt. Egenskapsnamn för delversionsnummer i Veeva Vault. Standardvärdet är `minor_version_number__v`.
17. Valfritt. Vevaevavalvets relationstypvärde. Alla resurser som läggs till på sidan representeras som relaterade baserat på det här värdet. Standardvärdet är `supporting_document__c`.

#### Fliken Sida

Om du synkroniserar sidor fyller du i följande på sidfliken:

![Fliken Sida](assets/page-tab.png)

1. Obligatoriskt. Mappa en egenskap från AEM till Veeva.
AEM egenskapsnamn. Kan väljas bland AEM egenskaper. (till exempel `jcr:title`) `{name}` kan mallas.
b. Veeva-egenskapsnamnet som anges exakt finns i Veeva. (till exempel `name__v`)\
   c. Egenskapstyp. Antingen `Text` eller `Multiline Text`.

2. Obligatoriskt. Mappa en egenskap från Veeva till AEM.
a. Veeva-egenskapsnamnet som anges exakt finns i Veeva. (till exempel `name__v`) b. AEM egenskapsnamn. Kan väljas bland AEM egenskaper. (till exempel `jcr:title`) c. Egenskapstyp. Antingen `Text` eller `Multiline Text`.


#### Fliken Resurser

Om du synkroniserar resurser ska du fylla i följande på fliken Resurser:

![Fliken Resurser](assets/asset-tab.png)

1. Obligatoriskt. Mappa en egenskap från AEM till Veeva.
AEM egenskapsnamn. Kan väljas bland AEM egenskaper. (till exempel `/jcr:content/metadata/jcr:title`) `{name}` kan mallas.
b. Veeva-egenskapsnamnet som anges exakt finns i Veeva. (till exempel `name__v`) c. Egenskapstyp. Antingen `Text` eller `Multiline Text`.

2. Obligatoriskt. Mappa en egenskap från Veeva till AEM.
a. Veeva-egenskapsnamnet som anges exakt finns i Veeva. (till exempel `name__v`) b. AEM egenskapsnamn. Kan väljas bland AEM egenskaper. (till exempel `/jcr:content/metadata/jcr:title`) c. Egenskapstyp. Antingen `Text` eller `Multiline Text`.

### Ytterligare inställningar

#### Skapa AEM

Vid generering av PDF/bild måste en AEM användare skapas för att hämta sidor från AEM. Skapa och ge skrivskyddade behörigheter till en användare genom att följa dessa länkar:

Om du använder AEM 6.5.5+:

* [Skapa en användare i AEM](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/setup-organize-users/adding-configuring-users.html?#create-a-user)
* [Lägga till behörigheter till en användare i AEM](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?#permissions-in-aem)

Om du använder AEM Cloud Service:

* [Hantera användare med AEM Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?#accessing)

Följande behörigheter krävs för den AEM tjänstanvändaren på det innehåll som ska konverteras till PDF/Image och skickas till Veeva:

* Läs

>[!IMPORTANT]
>
> Dessa åtgärder måste utföras som administratör för varje system.
> Du måste följa organisationens säkerhetsstandarder när du skapar användare och anger behörigheter.
>

#### Veeva - Skapa användare

För att kunna använda den här integreringen måste en användare skapas i Veeva Vault. Så här skapar du en användare:

1. Navigera till Admin -> Användare och grupper -> Valvanvändare -> Skapa

   ![Navigera till Veeva User](assets/veeva-user-navigate.png)

2. Fyll i de indata som behövs. Den enklaste konfigurationen är att ställa in `License Type` till `Full User` och `Security Profile` till `Vault Owner`. Spara när du är klar.

   ![Skapa veeva-användare](assets/veeva-user-create.png)

Följande behörigheter krävs för de specifika veva-dokumenttyper som används:

* Skapa/läsa dokument
* Skapa/läs versioner
* Skapa/uppdatera metadata
* Skapa/uppdatera återgivningar

>[!IMPORTANT]
>
> Dessa åtgärder måste utföras som administratör för varje system.
> Du måste följa organisationens säkerhetsstandarder när du skapar användare och anger behörigheter.
>
