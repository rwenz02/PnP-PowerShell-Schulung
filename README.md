# PnP Powershell Schulung

## Agenda 
* ### Was ist PnP PowerShell? 
* ### Welche Vorteile bietet PnP PowerShell? 
* ### Übersicht der wichtigsten Befehle
* ### Übungsaufgabe 
* ### Was ist die PnP Provisioning Engine?
* ### Warum nutzen wir die PnP Provisioning Engine?
* ### Übersicht über die Template Arten 
* ### Beispiele für verschiedene Templates
* ### Übersicht der verfügbaren Site Columns 
* ### Übungsaufgabe 

## Was ist PnP PowerShell? 
PnP PowerShell ist der Nachfolger des SharePointPnPPowerShellOnline Moduls. Es basiert auf .NET Core 3.1/.NET Framework 4.6.1 und beinhaltet über 600 Befehle zur Verwaltung von gängigen Microsoft Technologien wie SharePoint Online, MS Teams, MS Planner und MS Flow. Anders wie sein Vorgänger, das SharePointPnPPowerShellOnline Modul, unerstützt PnP PowerShell die Cross-Plattform Entwicklung und kann dementsprechend nicht nur auf Windows, sonder auch auf MacOS und Linux eingesetzt werden.

## Welche Vorteile bietet PnP PowerShell? 
* Vereinfachte Administration von SharePoint Online Umgebungen
* Über 600 Befehle
* Administrative Tätigkeiten können in wiederverwendbaren PowerShell Skripts zusammengefasst, oder direkt automatisiert werden
* Aktive Community stellt stetige Weiterentwicklung sicher

## Übersicht über die wichtigsten Befehle
* `Connect-PnPOnline [-Url] <String>` &rarr; Stellt eine Verbindung zu SharePoint Online her. Die Url gibt hierbei die entsprechende Site Collection an, zu welcher die Verbindung aufgebaut werden soll. Falls Adminrechte benötigt werden, muss die Url zum Admin-Center hinterlegt werden.
* `New-PnPSite [-Type] <String> [-Title] <String>` &rarr; Erstellt eine neue Site Collection. Der Parameter Type legt hierbei den Typ der Site Collection fest (z.B. CommunicationSite), der Parameter Title den Titel der Site Collection.
* `Add-PnPSiteCollectionAppCatalog [-Site] <String>` &rarr; Fügt einer Site Collection einen App Catalog hinzu. Der Parameter Site gibt hierbei die Site Collection an, für welche der App Catalog erstellt werden soll.
* `Add-PnPPage [-Name] <String> [-Title] <String>` &rarr; Fügt einer Site Collection eine Seite hinzu. Der Parameter Name legt den Namen, der Parameter Title den Titel der Seite fest.
* `Add-PnPApp [-Path] <String> [-Publish]` &rarr; Installiert eine App im App Catalog. Der Parameter Path ist hierbei der Pfad zu der lokal hinterlegten Datei (.sppkg). Publish stellt sicher, dass die App nach dem Hochladen auch direkt deployed wird.
* `Add-PnPTenantTheme [-Identity] <String> [-Palette] <ThemePalettePipeBind>` &rarr;  Spielt ein tenantweites Theme ein. Der Parameter Identity bestimmt den Namen des Themes, Palette erhält das Theme im JSON-Format.
* `New-PnPList [-Title] <String> [-Template] <String>` &rarr; Erstellt eine neue Liste. Title legt den Namen, Template den Typen der Liste fest (z.B. Announcements).
* `New-PnPSiteGroup [-Site] <String> [-Name] <String> [-PermissionLevels] <String[]>` &rarr; Erstellt eine neue Gruppe innerhalb der entsprechenden Site Collection. Der Parameter Name legt den Namen der Gruppe fest, Permission Level die Zugriffsberechtigung (z.B. Full Control).
* `Add-PnPGroupMember [-LoginName] <String> [-Group] <String>` &rarr; Fügt einen Nutzer einer bestimmten Gruppe hinzu. Der Parameter LoginName erhält hierbei den Login Namen des Nutzers, welcher hinzugefügt werden soll, Group den Namen der entsprechenden Gruppe. 

## Übungsaufgabe 
1. Installiere das PnP-PowerShell Modul mit folgendem befehl: `Install-Module -Name PnP.PowerShell`
2. Erstelle ein PowerShell Skript, welches als Übergabeparameter eine Url zum SharePoint Online Admin-Center erhält und daraufhin folgende Tätigkeiten ausführt: 
	1. Eine Site Collection namens "PnP Powershell" wird erstellt 
	2. Die Site Collection "PnP Powershell" erhält einen Site Collection App Catalog 
	3. Die Site Collection "PnP Powershell" erhält eine neue Seite namens "PnP PowerShell Schulung"
	4. Auf der Seite "PnP PowerShell Schulung" wird die App "PnP PowerShell Schulung App" aus dem Ordner "Apps" installiert 
	5. Auf der Seite "PnP PowerShell Schulung" wird das Theme "PnP PowerShell Schulung Theme" aus dem Ordner "Themes" eingespielt 
	6. Die Site Collection "PnP PowerShell" erhält eine neue Liste namens "Ankuendigungen" vom Template Typ `Announcements` 
	8. Eine neue SharePoint Gruppe namens "Schulungsteilnehmer" mit Zugriffslevel "Full Control" wird auf der Site Collection "PnP PowerShell" erstellt 
	9. Der aktuelle Tenant Admin wird der Gruppe "Schulungsteilnehmer" hinzugefügt
	
## Was ist die PnP Provisioning Engine? 
Die PnP Provisioning Engine enstand innerhalb der Microsoft 365 Platform Community (eine Open Source Intiative von Microsoft) und ermöglicht es, wiederverwendbare Templates für SharePoint Online im XML Format zu erstellen und anschließend über PnP PowerShell auf der entsprechenden Umgebung bereitzustellen. 

## Welche Vorteile bietet die PnP Provisioning Engine?
* Auslagern von bestehenden Inhalten unter SharePoint Online in XML Templates, welche anschließend wiederverwendet werden können 
* Erstellen von neuen Inhalten durch XML Templates, welche anschließend unter SharePoint Online eingespielt werden können
* Beschränkt sich nicht nur auf SharePoint Online, sondern wird auch von anderen MS Technologien unterstützt (z.B. MS Teams)
* Neue Updates auf monatlicher Basis

## Übersicht über die Template Arten
Die Templates der PnP Provisioning Engine können für folgende Elemente verwendet werden: 
* Site Columns
* Content Types
* Listen 
* Seiten 
* etc.

Wichtig ist hierbei zwischen folgenden Template Typen zu unterscheiden: 
* Site Templates 
* Tenant Templates 

Site Templates beschränken sich, wie der Name bereits verrät, lediglich auf eine bestimmte Site Collection der SharePoint Online Umgebung, d.h. alle Site Columns, Content Types, Listen, etc. welche angelegt werden, sind nur auf der hinterlegten Site Collection verfügbar. 

Tenant Templates erlauben es, Templates über den Site Scope hinaus auf dem ganzen Tenant bereit zu stellen. So können beispielsweise Site Designs, Themes, etc. auf Tenant Ebene eingespielt und anschließend von allen Site Collections des Tenants bezogen werden.

## Beispiele für verschiedene Templates
Beispiele für verschiedene Templates lassen sich im Ordner "Templates" finden.

## Übersicht der verfügbaren Site Columns
Eine Übersicht aller verfügbaren Site Columns unter der PnP Provisioning Engine lässt sich im Ordner "Site Columns" finden.

## Übungsaufgabe 
1. Erstelle ein XML-Template für deine Site Columns mit folgenden Spalten: 
	1. Beschreibung (mehrzeiliger Text) 
	2. Startdatum (Datum)
	3. Enddatum (Datum)
	4. Teilnehmer (Person)
	5. Kategorie (Taxonomy)
	6. Aktiv (Ja/Nein)
2. Erstelle einen Content Type namens "TermineCT" und füge ihm deine ersten 4 Site Columns hinzu
3. Erstelle ein Listentemplate mit dem Namen "Termine" und hinterlege den Content Type "TermineCT"
4. Erstelle einen Content Type namens "AnkuendigungenCT" und füge ihm die letzten 2 Site Columns hinzu
4. Erstelle ein Pagetemplate namens "Ankuendigungen" und hinterlege den Content Type "AnkuendigungenCT"
5. Füge deinem Pagetemplate "Ankuendigungen" standardmäßig ein Text-WebPart mit Beispieltext (Lorem Ipsum) hinzu
4. Stelle alle Templates auf der Site Collection "PnP Powershell" mithilfe des PnP PowerShell Moduls bereit
