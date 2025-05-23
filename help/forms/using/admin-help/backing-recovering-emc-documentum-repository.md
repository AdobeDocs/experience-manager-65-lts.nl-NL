---
title: Back-ups maken van de EMC Documentum-opslagplaats en deze herstellen
description: In dit document worden de taken beschreven die nodig zijn om back-ups te maken van de EMC Documentum-opslagplaats die is geconfigureerd voor uw AEM-formulieromgeving.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 054d31c3-bd58-4596-8c06-4909d75e9569
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---

# Back-ups maken van de EMC Documentum-opslagplaats en deze herstellen {#backing-up-and-recovering-the-emc-documentum-repository}

In deze sectie worden de taken beschreven die nodig zijn om back-ups te maken van de EMC Documentum-opslagplaats die is geconfigureerd voor uw AEM-formulieromgeving.

>[!NOTE]
>
>In deze instructies wordt ervan uitgegaan dat AEM-formulieren met Connectors voor ECM en EMC Documentum Content Server geïnstalleerd en geconfigureerd zijn zoals vereist.

Voor zowel het back-up- als het herstelproces zijn er twee hoofdtaken:

* Back-up maken van (of herstellen van) de AEM-formulieromgeving.
* Back-up maken van (of herstellen van) de EMC Documentum Content Server.

>[!NOTE]
>
>Maak een back-up van uw AEM-formuliergegevens voordat u een back-up maakt van het EMC Documentum-systeem en herstel vervolgens het EMC Documentum-systeem voordat u de AEM-formulieromgeving herstelt.

## Softwarevereisten {#software-requirements}

Om de noodzakelijke back-uptaken uit te voeren op uw EMC Documentum Content Server, koopt u een geschikt hulpprogramma van derden, zoals EMC NetWorker van EMC of CYA SmartRecovery voor EMC Documentum van CYA. De volgende instructies beschrijven de stappen voor het gebruik van EMC NetWorker Module versie 7.2.2.

U hebt de volgende EMC NetWorker-modules nodig:

* NetWorker-module
* Wizard Configuratie NetWorker
* Wizard Configuratie van NetWorker-apparaat
* NetWorker Module voor het gegevensbestandtype dat door uw Server van de Inhoud wordt gebruikt
* NetWorker Module voor Documentum

## De EMC Document Content Server voorbereiden voor back-up en herstel {#preparing-the-emc-document-content-server-for-backup-and-recovery}

In dit gedeelte wordt beschreven hoe u de EMC NetWorker-software op de Content Server kunt installeren en configureren.

**Bereid de EMC Documentum server voor steun** voor

1. Installeer op de EMC Documentum Content Server de EMC NetWorker-modules en accepteer alle standaardinstellingen.

   Tijdens de installatieprocessen, wordt u ertoe aangezet om de servernaam van de computer van de Server van de Inhoud als *Naam van de Server NetWorker* in te gaan. Wanneer u de EMC NetWorker Module voor uw database installeert, kiest u een volledige installatie.

1. Gebruikend de steekproefinhoud hieronder, creeer een configuratiedossier genoemd *nsrnmd_win.cfg* en bewaar het aan een toegankelijke plaats op de Server van de Inhoud. Dit bestand wordt aangeroepen door de opdrachten voor back-up en herstel.

   De volgende tekst bevat opmaaktekens voor regeleinden. Als u deze tekst naar een locatie buiten dit document kopieert, kopieert u een gedeelte per keer en verwijdert u de opmaaktekens wanneer u deze op de nieuwe locatie plakt.

   ```shell
    ################################################
    # NetWorker Module for Documentum v1.2 nsrnmd_win.cfg D5.3+ example with
    # typical set of working parameters.  THIS FILE MUST BE SITE-CUSTOMISED.
    #
    # Parameters not shown can be set in this file (as per site customisation) #or from the command-line.
    #
    # See the user Guides for details on all parameters, including
    # those not listed below.
    # Note: DCTM environment for D6 is slightly different from D5, refer to D6
    # Installation Guide to update the values.
    ################################################
    #Can get values for most of below from doing as the dctm inst owner: cmd> set DOCUMENTUM=C:\Documentum
    DM_HOME=C:\Documentum\product\6.0
    JAVA_HOME=C:\Progra~1\Documentum\java\1.5.0_12
    JAVA_PATH=C:\Progra~1\Documentum\java\1.5.0_12\bin
    PATH=C:\WINNT\system32;C:\WINNT;C:\WINNT\system32\WBEM;C:\Documentum\product\6.0\bin;C:\Documentum\fulltext\fast;C:\Documentum\product\6.0\fusion;C:\Program Files\Documentum\Shared;C:\Program Files\Legato\nsr\bin;C:\Program Files\Microsoft SQL Server\80\Tools\Binn;C:\Program Files\Microsoft SQL Server\90\DTS\Binn\;C:\Program Files\Microsoft SQL Server\90\Tools\binn;C:\Program Files\Microsoft SQL Server\90\Tools\Binn\VSShell\Common7\IDE;C:\Program Files\Documentum\java\1.5.0_12\bin;C:\Documentum\config;C:\Documentum
    #See also manifest dctm.jar file for class path locations
    CLASSPATH=.;C:\Program Files\Legato\nsr\bin;C:\Program Files\Legato\nsr\bin\nsrnmdde.jar;C:\Program Files\Documentum\java\1.5.0_12\lib\tools.jar;C:\Program Files\Documentum\Shared\dfc.jar;C:\Program Files\Documentum\Shared\aspectjrt.jar;C:\Program Files\Documentum\dctm.jar;C:\Program Files\Documentum\Shared\workflow.jar;C:\Program Files\Documentum\Shared\log4j.jar;C:\Program Files\Documentum\java\1.5.0_12\lib\dt.jar;C:\Documentum\config
   
    ################################################
    #If not using nsrnmdsv -m ALL|DB|DB_LOG|FTI|FTI_ALL|ICF|SA|SA_ALL, set #for backup
    NMD_SCOPE=ALL
    #Mandatory when scope (backup or restore) is FTI/SA without -a option
    #NMD_OBJECT_NAME=filestore_01
    ################################################
    NMDDE_DM_DOCBASE=Docbase
    NMDDE_DM_USER=Administrator
    #NMDDE_DM_PASSWD must be set via running: nsrnmdsv -f <nmdcfg> -P <pwd>.
    ################################################
    #DB related hooks to invoke arbitrary scripts:
    #Set if DB is on a remote host
    #NMD_DB_HOST=dbhost
    #Pure basename implies remote host execution; absolute path ... local
    #execution as in NMD v1.0.
    #
    #Remote execution requires script be put in remote nsrexecd bin directory
    #and D5.3+ host be added to remote nsr\res\servers file w/ nsrexecd recycled
    #
    #Refer to user Guides for sample script code.
    NMD_DB_FULL_BACKUP_CMD=C:\DocumentumBackup\Scripts\nsrnmddbf.bat
    NMD_DB_LOG_BACKUP_CMD=C:\DocumentumBackup\Scripts\nsrnmddbl.bat
    NMD_DB_INCR_BACKUP_CMD=C:\DocumentumBackup\Scripts\nsrnmddbi.bat
    ################################################
    #For D5.3+ only: NMD_FTI_INCLUDED, NMD_FTI_HOST, NMD_FTI_USER,
    #NMD_FTI_PASSWD & NMD_FTI_SUBDIRS.
    #Optional for remote D5.3+ FTI server
    NMD_FTI_INCLUDED=no
    #NMD_FTI_HOST=ftihost
    #Recommended for D5.3+ FTI server quiesce/unquiesce
    #NMD_FTI_USER=ftiadmin
    #The index name: optional for D5.3+ FTI server, used with -M FTI_ALL or
    #-M ALL
    #NMD_FTI_NAME=rep_name_ftindex_01
    #Recommended for D5.3+ FTI server quiesce/unquiesce
    #NMDDE_FTI_PASSWD must be set via running: nsrnmdsv -f <nmdcfg> -P <pwd>
    #-M FTI.
    #Pure basename implies remote host execution; absolute path ... local execution
    #as in NMD v1.0.
    #
    #Remote execution requires script be put in remote nsrexecd bin directory
    #and D5.3+ host be added to remote nsr\res\servers file w/ nsrexecd
    #recycled.
    #
    #See example nsrnmdfti*.bat examples.
    #
    #Mandatory for D5.3+
    #NMD_BACKUP_FTI_QUIESCE=nsrnmdftiq.bat
    #NMD_BACKUP_FTI_UNQUIESCE=nsrnmdftiu.bat
    #Used for D5.3+ to get InstallProfile.xml FTI file in multinode
    #discovery.
    #Optional, if not specified, will treat as single-node FTI.
    #NMD_FTI_GET_INSTPROF=nsrnmdfti_instprof.bat
    #Mandatory for D5.3+. No spaces in paths or around comma separators.
    #For remote FTI, paths must be valid at the FTI host.
    #NMD_FTI_SUBDIRS=F:\Documentum_idx\data\fulltext\fixml,F:\Documentum_idx
    #\data\fulltext\index
    ################################################
    #Mandatory. No spaces in paths or before comma
    #separators in NMD_ICF_SUBDIRS_xxx:
    #NMD_ICF_INCLUDED=yes
    #NMD_ICF_SUBDIRS=C:\Documentum\dba,C:\Documentum\product\5.3
    ################################################
    NMD_FILEREPORT_INCLUDED=yes
    NMDDE_METADATA_OUTPUT_DEST=C:\docbase_freports\
    ################################################
    #Other misc recommended NMD_xxx parameters
    #Recommended to get more meaningful saveset names
    NMD_USE_DEFAULT_SAVESET_NAMES=yes
    #Use following to skip unwanted ICF, FTI and non-SnapImage SA dirs/files.
    #For example, "<</>> +skip: dm_ftwork_dir" line will skip non-data
    #files.
    #
    #The path will be the same and must exist on D5.3+, remote FTI host, and
    #RCS hosts correspondingly if used.
    #NMD_DIRECTIVES_FILE=E:\Program Files\Legato\nsr\res\nsrnmddirectives.txt
    #For non-SnapImage SA backup
    #NMD_SA_FULL_NUM_SAVESET=16
    #NMD_SA_INCR_NUM_SAVESET=4
    #NMD_USE_SNAPIMAGE=yes
    ################################################
    # DSA setup
    ################################################
    # Name of the config file at the remote sites;
    # Mandatory, listed in the config file at the primary host.
    # (if skipped, backup is treated as local)
    # NMD_RCS_CFG_FILE=rep_name_rcs.cfg
   
    # SA-host mapping add, optional, will override far-store list info.
    # No space around comma.
    # NMD_HOST_SAS_MAP=host01,sa_01,sa_02
    # NMD_HOST_SAS_MAP=host02,sa_03
    ################################################
    NSR_SERVER=con-dctm
    #NSR_CLIENT=d5svrhost
    NSR_GROUP=Default
    NSR_DATA_VOLUME_POOL=Default
    #NSR_SNAPIMAGE_DATA_VOLUME_POOL=Default
    #Relocation dir will be the same on D5+ and remote FTI/SA hosts.
    NSR_RELOCATION=C:\reloc
    #NSR_PARALLELISM=16
    NSR_DEBUG_FILE=C:\Program Files\Legato\nsr\applogs\nmd.log
    NSR_DEBUG_LEVEL=9
    ################################################
    NMDDE_DM_PASSWD=XAtup9pl
   ```

   Laat het wachtwoordveld voor het configuratiebestand `NMDDE_DM_PASSWD` leeg. In de volgende stap stelt u het wachtwoord in.

1. Stel het wachtwoord voor het configuratiebestand als volgt in:

   * Open een opdrachtprompt en ga naar `[NetWorker_root]\Legato\nsr\bin` .
   * Voer het volgende bevel in werking: `-nsrnmdsv.exe -f`*&lt;path_to_cfg_file> - P &lt;password>*

1. Maak de uitvoerbare batchbestanden (.bat) die worden gebruikt om een back-up van de database te maken. (Zie de documentatie van NetWorker.) Stel de details in de batchbestanden in op basis van uw installatie.

   * Volledige back-up van database (nsrnmddbf.bat):

     `NetWorker_database_module_root` `-s`*&lt;NetWorker_Server_Name>* `-U` `[username]` `-P`*[ wachtwoord ]*`-l full`* &lt;database_name> *

   * Incrementele back-up van databases (nsrnmddbi.bat):

     `[NetWorker_database_module_root]` `-s`*&lt;NetWorker_Server_Name>* `-U` `[username]` `-P` `[password]` `-l 1 -R`*&lt;database_name>*

   * Back-up van databaselogbestand (nsrnmddbl.bat):

     `[NetWorker_database_module_root]` `-s` `<NetWorker_Server_Name>` `-U` `[username]` `-P` `[password]` `-l incr -R`*&lt;database_name>*

     Waarbij:

     `[NetWorker_database_module_root]` is de installatiemap van de NetWorker-module. Bijvoorbeeld, is de standaardinstallatiemap voor Module NetWorker voor SQL Server C:\Program Files\Legato\nsr\bin\nsrsqlsv.

     `NetWorker_Server_Name` is de server waarop NetWorker is geïnstalleerd.

     `username` en `password` zijn de gebruikersnaam en het wachtwoord van de databasebeheergebruiker.

     `database_name` is de naam van de database waarvan een back-up moet worden gemaakt.

**creeer een reserveapparaat**

1. Maak een directory op de EMC Documentum-server en deel de map door alle gebruikers volledige rechten te geven.
1. Start EMC NetWorker Administrator en klik op Mediabeheer > Apparaten.
1. Klik met de rechtermuisknop op Apparaten en selecteer Maken.
1. Voer de volgende waarden in en klik op OK:

   **Naam:** de volledige weg van de gedeelde folder

   **Type van Media:** `File`

1. Klik met de rechtermuisknop op het nieuwe apparaat en selecteer Bewerkingen.
1. Klik op Label, voer een naam in, klik op OK en klik vervolgens op Onderbrengen.

Er wordt een apparaat toegevoegd waarop de back-upbestanden worden opgeslagen. U kunt meerdere apparaten met verschillende indelingen toevoegen.

## Back-up maken van de EMC Documentum Content Server {#back-up-the-emc-documentum-content-server}

Voer de volgende taken uit nadat u een volledige back-up van uw AEM-formuliergegevens hebt gemaakt. (Zie [ Steunend de de vormengegevens van AEM ](/help/forms/using/admin-help/backing-aem-forms-data.md#backing-up-the-aem-forms-data).)

>[!NOTE]
>
>De bevelmanuscripten vereisen de volledige weg aan het nsrnmd_win.cfg- dossier dat u in [ creeerde het Voorbereiden van de EMC Server van de Inhoud van het Document voor steun en terugwinning ](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery).

1. Open een opdrachtprompt en ga naar `[NetWorker_root]\Legato\nsr\bin` .
1. Voer de volgende opdracht uit:

   ```shell
    - nsrnmdsv.exe -f <path_to_cfg_file>
   ```

## De EMC Documentum Content Server herstellen {#restore-the-emc-documentum-content-server}

Voer de volgende taken uit voordat u de gegevens van uw AEM-formulieren herstelt. (Zie [ Herstellend de de vormengegevens van AEM ](/help/forms/using/admin-help/recovering-aem-forms-data.md#recovering-the-aem-forms-data).)

>[!NOTE]
>
>De bevelmanuscripten vereisen de volledige weg aan het nsrnmd_win.cfg- dossier dat u in [ creeerde het Voorbereiden van de EMC Server van de Inhoud van het Document voor steun en terugwinning ](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery).

1. Stop de Docbase-service die u wilt herstellen.
1. Begin het nut van de Gebruiker NetWorker voor uw gegevensbestandmodule (bijvoorbeeld, *Gebruiker NetWorker voor SQL Server*).
1. Klik op het gereedschap Herstellen en selecteer vervolgens Normaal.
1. Selecteer links in het scherm de database voor uw Docbase en klik op de knop Start op de werkbalk.
1. Start de Docbase-service opnieuw wanneer de database is hersteld.
1. Open een bevelherinnering en verandering in *[NetWorker_root]* \Legato\nsr\bin
1. Voer de volgende opdracht uit:

   ```shell
    - nsrnmdrs.exe -B <docbase_name> -f <path_to_cfg_file> -C SA
   ```
