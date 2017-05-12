---
title: "Panoramica di Visual Studio Tools per Office Runtime"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "runtime Office [sviluppo per Office in Visual Studio], informazioni"
  - "VSTOLoader.dll"
  - "caricatore di runtime [sviluppo per Office in Visual Studio]"
  - "runtime Office [sviluppo per Office in Visual Studio], assembly"
  - "runtime Office [sviluppo per Office in Visual Studio]"
  - "runtime [sviluppo per Office in Visual Studio], assembly"
  - "vstoee.dll"
  - "Runtime di Visual Studio Tools per Office"
  - "soluzioni Office [sviluppo per Office in Visual Studio], runtime"
  - "soluzioni [sviluppo per Office in Visual Studio], runtime"
  - "versioni [sviluppo per Office in Visual Studio], runtime"
  - "assembly [sviluppo per Office in Visual Studio], runtime"
  - "runtime [sviluppo per Office in Visual Studio], informazioni sul runtime VSTO"
  - "caricatore di soluzioni [sviluppo per Office in Visual Studio]"
  - "runtime [sviluppo per Office in Visual Studio]"
ms.assetid: 5526a4d2-a61c-43ee-8349-dd1968e0cdb4
caps.latest.revision: 92
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 91
---
# Panoramica di Visual Studio Tools per Office Runtime
  Per eseguire soluzioni create usando gli strumenti di sviluppo di Microsoft Office in Visual Studio, Visual Studio 2010 Tools per Office Runtime deve essere installato nei computer degli utenti finali. Per altre informazioni, vedere [Procedura: installare il runtime ridistribuibile di Microsoft Visual Studio Tools per Office](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Visual Studio 2010 Tools per Office Runtime è costituito da due componenti principali:  
  
-   Le estensioni di Office per .NET Framework. Questi componenti sono assembly gestiti che forniscono il livello di comunicazione tra la soluzione e l'applicazione di Microsoft Office. Per altre informazioni, vedere [Estensioni di Office per .NET Framework](#officeextensions).  
  
-   Il caricatore di soluzioni Office. Questo componente è un set di DLL non gestite che le applicazioni di Office usano per caricare il runtime e le soluzioni. Per altre informazioni, vedere [Informazioni sul caricatore di soluzioni Office](#UnmanagedLoader).  
  
 È possibile installare il runtime in numerose modalità diverse. A seconda della configurazione del computer, al momento dell'installazione del runtime vengono installati componenti di runtime diversi. Per altre informazioni, vedere [Scenari di installazione del runtime di Visual Studio Tools per Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
##  <a name="officeextensions"></a> Estensioni di Office per .NET Framework  
 Visual Studio 2010 Tools per Office Runtime include estensioni Office per .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e versioni successive. Nelle soluzioni destinate a ciascuna versione di .NET Framework vengono usate le estensioni appropriate per la versione interessata.  
  
 Queste estensioni sono costituite da assembly usati dalle soluzioni per automatizzare ed estendere le applicazioni di Office. Quando si crea un progetto di Office, in Visual Studio vengono automaticamente aggiunti riferimenti agli assembly usati per il tipo di progetto e .NET Framework di destinazione del progetto. Per altre informazioni sugli assembly nelle estensioni di Office, vedere [Assembly nel runtime di Visual Studio Tools per Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
### Differenze di progettazione nelle estensioni di Office  
 La maggior parte dei tipi usati nelle estensioni di Office per .NET Framework 3.5 sono classi. Si tratta delle stesse classi incluse nelle versioni precedenti di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. La maggior parte dei tipi usati nelle estensioni Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive è costituita invece da interfacce. Ad esempio, quando si usa [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, i tipi <xref:Microsoft.Office.Tools.Excel.Worksheet> e <xref:Microsoft.Office.Tools.Word.Document> sono interfacce anziché classi.  
  
 Nella maggior parte dei casi, il codice che si scrive nelle soluzioni Office è lo stesso sia che la soluzione venga destinata a .NET Framework 3.5 o a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Tuttavia, alcune funzionalità richiedono codice diverso quando si ha come destinazione versioni diverse di .NET Framework. Per altre informazioni, vedere [Migrazione di soluzioni Office a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
### Interfacce nelle estensioni Office per .NET Framework 4 o versioni successive  
 La maggior parte delle interfacce nelle estensioni Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive non è studiata per essere implementata dal codice utente. Le uniche interfacce che è possibile implementare direttamente hanno nomi che iniziano con la lettera **I**, ad esempio <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.  
  
 Tutte le interfacce che non iniziano con la lettera **I** sono implementate internamente da Visual Studio 2010 Tools per Office Runtime; queste interfacce potrebbero cambiare nelle versioni future. Per creare oggetti che implementano tali interfacce, usare i metodi forniti dall'oggetto Globals.Factory nel progetto. Ad esempio, per ottenere un oggetto che implementa l'interfaccia <xref:Microsoft.Office.Tools.Excel.SmartTag>, usare il metodo Globals.Factory.CreateSmartTag. Per altre informazioni su Globals.Factory, vedere [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### Abilitazione dell'equivalenza dei tipi e dei tipi incorporati in progetti destinati a .NET Framework 4 o versione successiva  
 Poiché il modello a oggetti delle estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva è basato su interfacce, è possibile usare la funzionalità di equivalenza dei tipi sia in Visual C\# che in Visual Basic in Visual Studio per incorporare nella soluzione informazioni sul tipo da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Questa funzionalità consente alle soluzioni Office e a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] di eseguire il controllo della versione in modo indipendente. Se ad esempio la soluzione usa l'interfaccia <xref:Microsoft.Office.Tools.Word.Document> come tipo incorporato e la versione successiva del runtime aggiunge membri all'interfaccia <xref:Microsoft.Office.Tools.Word.Document>, la soluzione funzionerà comunque con la versione successiva del runtime. Se la soluzione non usa l'interfaccia <xref:Microsoft.Office.Tools.Word.Document> come tipo incorporato, non funzionerà più con la versione successiva del runtime.  
  
 Per impostazione predefinita, la funzionalità di equivalenza dei tipi non è abilitata quando si crea un progetto di Office destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva. Se si desidera abilitare tale funzionalità, impostare la proprietà **Incorpora tipi di interoperabilità** di uno qualsiasi dei seguenti riferimenti all'assembly nel progetto su **True**:  
  
-   Microsoft.Office.Tools.dll  
  
-   Microsoft.Office.Tools.Common.dll  
  
-   Microsoft.Office.Tools.Excel.dll  
  
-   Microsoft.Office.Tools.Outlook.dll  
  
-   Microsoft.Office.Tools.Word.dll  
  
 Dopo avere effettuato tale modifica, le informazioni sul tipo per tutti i tipi di runtime usati dal progetto vengono incorporate nell'assembly della soluzione quando il progetto viene compilato. In fase di esecuzione, la soluzione usa tali informazioni sul tipo incorporato, anziché le informazioni sui tipi negli assembly a cui si fa riferimento.  
  
##  <a name="UnmanagedLoader"></a> Caricatore di soluzioni Office  
 Il runtime di Visual Studio Tools per Office include molte DLL non gestite che nelle applicazioni di Office servono a caricare il runtime e le soluzioni Office. Anche se non si lavora mai direttamente con queste DLL, conoscerne lo scopo può permettere di comprendere meglio l'architettura delle soluzioni Office.  
  
 Per informazioni sull'uso di questi componenti durante il processo di caricamento, vedere [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md) e [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### VSTOEE.dll  
 Quando un utente apre una personalizzazione a livello di documento o avvia un componente aggiuntivo VSTO, l'applicazione di Office effettua la chiamata a VSTOEE.dll per eseguire le attività richieste per caricare [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 VSTOEE.dll verifica che venga caricata la versione corretta di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] per la soluzione e la versione installata di Office. Anche se è possibile installare più versioni di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nello stesso computer, viene installata solo un'istanza di VSTOEE.dll alla volta, ossia quella inclusa nella versione più recente del runtime installato nel computer. Per altre informazioni sulle diverse versioni di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che è possibile usare per altre soluzioni, vedere [Esecuzione di soluzioni in versioni diverse di Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
### VSTOLoader.dll  
 Dopo il caricamento da parte di VSTOEE.dll della versione appropriata di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], VSTOLoader.dll esegue la maggior parte delle operazioni necessarie per caricare l'assembly della soluzione. VSTOLoader.dll consente di effettuare quanto riportato di seguito:  
  
-   Creare un dominio dell'applicazione per ogni assembly della soluzione.  
  
-   Eseguire un set di controlli di sicurezza per verificare che l'assembly della soluzione disponga delle autorizzazioni per l'esecuzione.  
  
-   Caricare la versione delle estensioni di Office per .NET Framework richiesta dalla soluzione.  
  
 VSTOLoader.dll consente anche di eseguire alcune operazioni specifiche dei componenti aggiuntivi VSTO:  
  
-   Implementa l'interfaccia <xref:Extensibility.IDTExtensibility2>.<xref:Extensibility.IDTExtensibility2> è un'interfaccia COM che deve essere implementata da tutti i componenti aggiuntivi VSTO per le applicazioni di Microsoft Office. Questa interfaccia definisce i metodi chiamati dall'applicazione per comunicare con il componente aggiuntivo VSTO.  
  
-   Implementa l'interfaccia IManagedAddin. Questa interfaccia viene usata dalle applicazioni di Office per consentire il caricamento di componenti aggiuntivi VSTO. Per altre informazioni, vedere [Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md).  
  
## Informazioni sulle versioni a 32 bit e a 64 bit del runtime  
 Esistono versioni distinte a 64 bit e a 32 bit di Visual Studio 2010 Tools per Office Runtime. Tali versioni del runtime vengono usate per eseguire soluzioni in edizioni di Office a 64 bit e a 32 bit. Nella tabella seguente viene illustrata la versione del runtime richiesta per ogni combinazione di Windows e Office.  
  
|Edizione di Windows|Edizione di Microsoft Office|Versione richiesta del runtime di Visual Studio Tools per Office|  
|-------------------------|----------------------------------|----------------------------------------------------------------------|  
|32 bit|32 bit|32 bit|  
|64 bit|32 bit|64 bit|  
|64 bit|64 bit|64 bit|  
  
 Quando si installa Office, la versione richiesta di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene installata insieme a Office. Ad esempio, quando si installa l'edizione a 64 bit di Office in una versione a 64 bit di Windows, viene installata anche la versione a 64 bit di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Per altre informazioni sull'installazione di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] con Office, vedere [Scenari di installazione del runtime di Visual Studio Tools per Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 La versione a 64 bit di Office può eseguire anche soluzioni Office create mediante modelli di progetto per Microsoft Office System 2007 in Visual Studio 2008. Non è tuttavia in grado di eseguire soluzioni Office create mediante modelli di progetto per Microsoft Office 2003 in Visual Studio 2008 né soluzioni Office create usando Visual Studio 2005. Per altre informazioni, vedere [Esecuzione di soluzioni in versioni diverse di Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
## Ripristino di Visual Studio 2010 Tools per Office Runtime  
 Se è necessario ripristinare il runtime, aprire **Programmi e funzionalità** o**Installazione applicazioni** nel Pannello di controllo, selezionare **Microsoft Visual Studio 2010 Tools per Office Runtime** nell'elenco di programmi, quindi fare clic su **Disinstalla**. Il programma di installazione che viene eseguito consente di ripristinare il runtime. Se si fa clic su **Cambia**, non viene fornita un'opzione per ripristinare il runtime.  
  
## Vedere anche  
 [Scenari di installazione del runtime di Visual Studio Tools per Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Assembly nel runtime di Visual Studio Tools per Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)   
 [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Aggiornamento e migrazione di soluzioni Office](../vsto/upgrading-and-migrating-office-solutions.md)  
  
  