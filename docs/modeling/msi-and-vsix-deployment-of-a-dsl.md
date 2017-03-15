---
title: "Distribuzione MSI e VSIX di un linguaggio DSL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 2
---
# Distribuzione MSI e VSIX di un linguaggio DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile installare un linguaggio specifico di dominio di diventi proprietaria del computer o in altri computer.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il valore è già installato nel computer di destinazione.  
  
##  <a name="which"></a> Scelta tra la distribuzione MSI e VSIX  
 Esistono due metodi per implementare un linguaggio specifico di dominio:  
  
|Metodo|vantaggi|  
|------------|--------------|  
|\(VSX[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione\)|Molto semplice distribuire: Copiare ed eseguire **.vsix** file dal progetto DslPackage.<br /><br /> Per ulteriori informazioni vedere [Installazione e disinstallazione di un modello DSL utilizzando il VSX](#Installing).|  
|MSI \(file MSI\)|-   Consente all'utente si apra [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fare doppio clic su un file di modello DSL.<br />-   Associare un'icona al tipo di file DSL nel computer di destinazione.<br />-   Associa uno XSD \(XML Schema\) al tipo di file DSL.  In questo modo si evita gli avvisi quando il file viene caricato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> È necessario aggiungere un progetto di installazione alla soluzione per creare un file MSI.<br /><br /> Per ulteriori informazioni, vedere [Implementando un modello DSL utilizzando un file MSI](#msi).|  
  
##  <a name="Installing"></a> Installazione e disinstallazione di un modello DSL utilizzando il VSX  
 Quando il modello DSL è installato con questo metodo, l'utente può aprire un file di modello DSL da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ma il file non può essere aperto da esplora risorse.  
  
#### Per installare un modello DSL utilizzando il VSX  
  
1.  Nel computer, trovare **.vsix** archiviare compilato dal progetto del pacchetto DSL.  
  
    1.  in **Esplora soluzioni**, fare clic con il pulsante destro del mouse  **DslPackage** proiettare quindi fare clic su  **aprire la cartella in Esplora risorse**.  
  
    2.  Individuare il file **bin\\\*\\***Progetto***.DslPackage.vsix**  
  
2.  copiare **.vsix** file nel computer di destinazione in cui si desidera installare il modello DSL.  Si può trattare del computer in uso o di un altro computer.  
  
    -   Il computer di destinazione deve avere una delle versioni di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] che supporta DSLs in fase di esecuzione.  Per ulteriori informazioni, vedere [Edizioni di Visual Studio per la visualizzazione e modellazione di SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   Il computer di destinazione deve avere una delle versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] originati  **DslPackage\\source.extensions.manifest**.  
  
3.  Nel computer di destinazione fare doppio clic sul file **.vsix**.  
  
     Verrà visualizzato **Visual Studio Extension Installer** e verrà installata l'estensione.  
  
4.  Avviare o riavviare [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
5.  Per testare il modello DSL, utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per creare un nuovo file con estensione cui è definito per il linguaggio DSL.  
  
#### Per disinstallare un modello DSL che è stato installato utilizzando VSX  
  
1.  Scegliere **Gestione estensioni** dal menu **Strumenti**.  
  
2.  Espandere **Estensioni installate**.  
  
3.  Selezionare l'estensione in cui il modello DSL è definito quindi fare clic su **disinstallare**.  
  
 Raramente, può verificarsi che un'estensione errata non venga caricata creando un rapporto nella finestra di errore. Tale estensione non viene però visualizzata in Gestione estensioni.  In tal caso, è possibile rimuovere l'estensione eliminando il file da:  
  
 *LocalAppData* **\\Microsoft\\VisualStudio\\10.0\\Extensions**  
  
##  <a name="msi"></a> Implementare un modello DSL in MSI  
 Definendo un file MSI \(Windows Installer\) per il linguaggio DSL, è possibile consentire agli utenti di aprire i file di modello DSL da esplora risorse.  È inoltre possibile associare un'icona e una breve descrizione con l'estensione di file.  Inoltre, il file MSI possibile installare uno XSD che può essere utilizzato per convalidare i file di modello DSL.  Se lo si desidera, è possibile aggiungere altri componenti in MSI che verrà installato contemporaneamente.  
  
 Per ulteriori informazioni sui file MSI e altre opzioni di distribuzione, vedere [Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).  
  
 Per compilare un'applicazione MSI, aggiungere un progetto di installazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione.  Il metodo più semplice di creare un progetto di installazione è utilizzare il modello di CreateMsiSetupProject.tt, che è possibile scaricare da [Sito VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### Per implementare un modello DSL in MSI  
  
1.  set `InstalledByMsi` nel manifesto dell'estensione.  Ciò impedisce il VSX siano installati e disinstallazione di dal file MSI.  Ciò è importante se si comprenderanno altri componenti in MSI.  
  
    1.  aprire DslPackage \\ source.extension.tt  
  
    2.  Inserire prima la seguente riga `<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  Creare o modificare l'icona che rappresenterà il modello DSL in Esplora risorse.  Ad esempio, modifica **DslPackage\\Resources\\File.ico**  
  
3.  Assicurarsi che i seguenti attributi del linguaggio DSL siano corretti:  
  
    -   Fare clic su sfoglia DSL il nodo radice e nella Finestra Proprietà, rivedere:  
  
        -   Descrizione  
  
        -   Versione  
  
    -   Fare clic su **editor** nodo, quindi nella Finestra Proprietà fare clic su  **icona**.  Impostare il valore per fare riferimento a un file di icona in **DslPackage\\Resources**, ad esempio  **File.ico**  
  
    -   In **Compilazione** menu, aprire  **Configuration Manager**quindi selezionare la configurazione che si desidera compilare, ad esempio  **rilasciare** o  **debug**.  
  
4.  andare a [La home page dell'SDK di visualizzazione e modellazione](http://go.microsoft.com/fwlink/?LinkID=186128)e da **download** scheda, download  **CreateMsiSetupProject.tt**.  
  
5.  aggiungere **CreateMsiSetupProject.tt** al progetto di Dsl.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà creato un file denominato  **CreateMsiSetupProject.vdproj**.  
  
6.  in Esplora risorse, copiare il Dsl \\\*.vdproj to a new folder named Setup.  
  
     \(Se lo si desidera, è ora possibile escludere CreateMsiSetupProject.tt dal progetto di Dsl\).  
  
7.  in **Esplora soluzioni**, aggiungere  **Setup\\\*.vdproj** come progetto esistente.  
  
8.  Scegliere **Dipendenze progetto** dal menu **Progetto**.  
  
     in **Dipendenze di progetto** la finestra di dialogo, selezionare il progetto di installazione.  
  
     selezionare la casella accanto a **DslPackage**.  
  
9. Ricompilare la soluzione.  
  
10. In Esplora risorse, individuare il file MSI generato nel progetto di installazione.  
  
     Copiare il file MSI in un computer in cui si desidera installare il modello DSL.  Fare doppio clic sul file MSI.  Il programma di installazione verrà eseguito.  
  
11. Nel computer di destinazione, creare un nuovo file con estensione di file del modello DSL.  Verificare gli aspetti seguenti:  
  
    -   Nella visualizzazione elenco di esplora risorse, viene visualizzato con l'icona e la descrizione che è definito.  
  
    -   Quando si fa doppio clic sul file, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà avviato e apre il file di modello DSL nell'editor DSL.  
  
 Se si preferisce, è possibile creare il progetto di installazione manuale, anziché il modello di testo.  Per una procedura dettagliata che include questa procedura vedere il capitolo 5 di [Lab dell'SDK di visualizzazione e modellazione](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### Per disinstallare un modello DSL installata da un file MSI  
  
1.  In windows, aprire **programmi e funzionalità** il Pannello di controllo.  
  
2.  Per disinstallare il modello DSL.  
  
3.  Riavviare Visual Studio.