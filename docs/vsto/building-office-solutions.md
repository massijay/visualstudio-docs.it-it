---
title: "Compilazione di soluzioni Office | Microsoft Docs"
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
  - "debug [sviluppo per Office in Visual Studio]"
  - "debug di applicazioni di Office in Visual Studio"
  - "soluzioni [sviluppo per Office in Visual Studio], debug"
  - "applicazioni di Office [sviluppo per Office in Visual Studio], debug"
  - "sviluppo di applicazioni [sviluppo per Office in Visual Studio], compilazione"
  - "applicazioni di Office [sviluppo per Office in Visual Studio], compilazione"
  - "progetti [sviluppo per Office in Visual Studio], debug"
  - "soluzioni Office [sviluppo per Office in Visual Studio], compilazione"
  - "soluzioni [sviluppo per Office in Visual Studio], compilazione"
  - "progetti di Office [sviluppo per Office in Visual Studio], debug"
  - "progetti [sviluppo per Office in Visual Studio], compilazione"
  - "compilazioni [sviluppo per Office in Visual Studio]"
  - "progetti di Office [sviluppo per Office in Visual Studio], compilazione"
  - "sviluppo di applicazioni [sviluppo per Office in Visual Studio], debug"
  - "soluzioni Office [sviluppo per Office in Visual Studio], debug"
ms.assetid: c4b79ea8-df70-4a72-b76e-26e337d65727
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Compilazione di soluzioni Office
  I processi di compilazione e debug dei progetti di Office sono in genere analoghi agli stessi processi per altri tipi di progetti in Visual Studio, ad esempio per Windows Form. Gli argomenti di questa sezione illustrano le differenze esistenti. Per informazioni generali sulla compilazione di applicazioni, vedere [Compilazione di applicazioni in Visual Studio](../ide/compiling-and-building-in-visual-studio.md).  
  
## Output del progetto per i progetti di Office  
 Il percorso di output per i progetti di Office è *nomeprogetto*\\bin\\release o *nomeprogetto*\\bin\\debug. Non è possibile eseguire la compilazione in una directory di distribuzione.  
  
### Progetti a livello di documento  
 Quando si compila un progetto a livello di documento, nell'output del progetto vengono inclusi gli elementi seguenti:  
  
-   Una copia del documento del progetto.  
  
-   L'assembly del progetto e tutti gli assembly di riferimento la cui proprietà **Copia localmente** è impostata su **true**.  
  
-   Il manifesto dell'applicazione, che ha l'estensione di file manifest. Per altre informazioni, vedere [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
-   Il manifesto della distribuzione, che ha l'estensione di file vsto. Per altre informazioni, vedere [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Un file di database di programma \(PDB\).  
  
> [!NOTE]  
>  Se si compila una soluzione a livello di documento in un percorso remoto anziché nel computer locale, aggiungere il percorso completo all'elenco di percorsi attendibili nel Centro protezione dell'applicazione. Per altre informazioni, vedere la sezione intitolata Concessione dell'attendibilità ai documenti in [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md).  
  
### Progetti a livello di applicazione  
 Quando si compila un progetto di componente aggiuntivo VSTO, nell'output del progetto vengono inclusi gli elementi seguenti:  
  
-   L'assembly del progetto e tutti gli assembly di riferimento la cui proprietà **Copia localmente** è impostata su **true**.  
  
-   Il manifesto dell'applicazione, che ha l'estensione di file manifest. Per altre informazioni, vedere [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
-   Il manifesto della distribuzione, che ha l'estensione di file vsto. Per altre informazioni, vedere [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Un file del database di programma \(PDB\) per l'assembly del progetto.  
  
 Il processo di compilazione per i progetti di componente aggiuntivo VSTO crea inoltre un set di voci del Registro di sistema nel computer di sviluppo, necessario per il caricamento del componente aggiuntivo VSTO. Per altre informazioni, vedere [Voci del Registro di sistema per i componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Se si compila un progetto di componente aggiuntivo VSTO per Outlook che contiene aree del modulo, il processo di generazione aggiunge al Registro di sistema le informazioni aggiuntive seguenti:  
  
-   Una chiave per ogni classe di messaggi associata a una o più aree del modulo.  
  
-   Una voce per ogni area del modulo e un valore associato che rappresenta il nome del componente aggiuntivo VSTO di Outlook.  
  
 Outlook necessita di queste informazioni per caricare le aree del modulo.  
  
## Assembly a cui viene fatto riferimento  
 È possibile fare riferimento agli assembly \(compresi i progetti Libreria di classi\) dal progetto Compilazione di soluzioni Office. Ogni assembly di riferimento ha una proprietà chiamata **Copia localmente**.**Copia localmente** indica se l'assembly viene copiato o meno nella directory di output. Per impostazione predefinita, questa proprietà è impostata su **true**. Ogni assembly di riferimento con la proprietà **Copia localmente** impostata su **true** viene copiato nella directory di output.  
  
## Sicurezza durante il processo di compilazione  
 Visual Studio configura automaticamente le impostazioni di sicurezza nel computer di sviluppo per concedere l'attendibilità alla soluzione durante il processo di compilazione. Ciò consente alla soluzione di essere eseguita mentre se ne esegue il debug.  
  
 I progetti di Office usano i certificati per verificare il server di pubblicazione. Visual Studio crea automaticamente un certificato temporaneo per identificare le soluzioni Office e configura il computer di sviluppo in modo da considerare attendibile il certificato temporaneo.  
  
 Per altre informazioni, vedere [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md).  
  
### Progetti di rete  
 Se il percorso dell'assembly o del documento si trova in una condivisione di rete, l'aggiornamento dei criteri di sicurezza locali \(livello utente\) non è sufficiente per consentire l'esecuzione della soluzione. Un amministratore dovrà infatti concedere agli assembly e ai documenti in una condivisione di rete l'attendibilità totale a livello di computer prima che la soluzione possa essere eseguita. Per altre informazioni sull'impostazione dei criteri di sicurezza, vedere [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md).  
  
 Per i progetti a livello di documento, è necessario aggiungere anche il percorso completo del documento all'elenco delle cartelle attendibili di Office. Per altre informazioni, vedere [Concessione dell'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).  
  
## Modifica della piattaforma di destinazione  
 Per impostazione predefinita, la piattaforma di destinazione per i progetti di Office è **Qualsiasi CPU**. In genere, non è consigliabile modificare questa impostazione. Le soluzioni Office compilate con l'impostazione della destinazione della piattaforma impostata su **Qualsiasi CPU** vengono eseguite nelle versioni a 32 bit e a 64 bit di Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
 È consigliabile impostare la destinazione della piattaforma su x64 solo se si crea una soluzione che verrà eseguita esclusivamente nelle versioni a 64 bit di Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] e se la soluzione chiama API native a 64 bit. Per altre informazioni sulla modifica dell'impostazione della destinazione della piattaforma, vedere [NIB: Procedura: Ottimizzare un'applicazione per un tipo di CPU specifico](http://msdn.microsoft.com/it-it/294a75d2-4279-4b72-8298-2bea05be907a).  
  
 Se si imposta la destinazione della piattaforma su x64, la soluzione non verrà eseguita nelle versioni a 32 bit di Windows o di Office. Per la destinazione della piattaforma x64 è necessario che la soluzione venga eseguita in un processo a 64 bit.  
  
## Uso del comando Pulisci  
 Per rimuovere dal computer di sviluppo i file di progetto compilati, è possibile usare il comando **Pulisci** dal menu **Compilazione** di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Il comando **Pulisci** elimina tutti i file presenti nel percorso di output di compilazione. Per i progetti a livello di applicazione il comando **Pulisci** consente inoltre di rimuovere le voci del Registro di sistema create dal processo di compilazione.  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Debug di progetti di Office](../vsto/debugging-office-projects.md)|Descrive i problemi relativi al debug dei progetti di Office.|  
|[Procedura dettagliata: creazione di una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Illustra come creare una personalizzazione di base a livello di documento per Excel.|  
|[Procedura: Riattivare un componente aggiuntivo VSTO disattivato](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Descrive come riabilitare un componente aggiuntivo VSTO che è stato disabilitato con o senza chiusura imprevista.|  
|[Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)|Fornisce i collegamenti a informazioni sulla creazione di soluzioni Office e sul ruolo degli assembly all'interno della soluzione.|  
  
  