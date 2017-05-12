---
title: "Sicurezza dei documenti nelle soluzioni a livello di documento"
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
  - "documenti [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "documenti Office [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "autorizzazioni [sviluppo per Office in Visual Studio]"
  - "autorizzazioni limitate [sviluppo per Office in Visual Studio]"
  - "cartelle di lavoro [sviluppo per Office in Visual Studio], autorizzazioni limitate"
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Sicurezza dei documenti nelle soluzioni a livello di documento
  Nei progetti a livello di documento è possibile utilizzare le funzionalità di sicurezza di Microsoft Office Word e Microsoft Office Excel.  Queste funzionalità impediscono la modifica di parti protette di un documento da parte di utenti non autorizzati.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Con Excel è possibile abilitare o disabilitare la sicurezza mentre la cartella di lavoro è aperta nella finestra di progettazione,   mentre con Word la sicurezza può essere attivata solo all'esterno della finestra di progettazione.  In fase di esecuzione è possibile abilitare o disabilitare la sicurezza a livello di codice sia per Word sia per Excel.  
  
 Quando viene attivata la sicurezza in un documento aperto nella finestra di progettazione, tutti i controlli vengono rimossi dalla **Casella degli strumenti** o resi non disponibili. Non sarà quindi possibile trascinare alcun elemento dalla finestra **Origini dati** al documento.  
  
## ServerDocument e documenti protetti  
 Se un documento è protetto, non sarà possibile accedere alla cache dei dati dall'esterno del documento  e non sarà possibile utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per recuperare o manipolare i dati memorizzati nella cache in un documento protetto né utilizzare altri metodi della classe <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>.  
  
## Sicurezza di documenti di Word nella finestra di progettazione  
 Se si aggiunge la sicurezza in un documento o in un modello di Word aperto in Visual Studio, non sarà possibile attivarla nella finestra di progettazione.  Il documento aperto in Visual Studio è in modalità progettazione, ma per poter attivare la sicurezza il documento deve essere in modalità esecuzione.  
  
 Tuttavia, se si crea un progetto che utilizza un documento di Word esistente con la sicurezza attivata, tale documento sarà protetto anche se aperto nella finestra di progettazione.  Le parti protette del documento non potranno essere modificate, ma sarà comunque possibile scrivere il codice nell'editor di codice per automatizzare il documento.  Inoltre, non sarà possibile compilare il progetto se la sicurezza è attivata mentre il documento è aperto in Visual Studio.  
  
 È possibile disattivare la sicurezza mentre il documento è aperto nella finestra di progettazione per consentirne la modifica e per compilare il progetto.  Durante il debug non è possibile disattivare la sicurezza nella copia aperta nella finestra di progettazione. Il documento che viene aperto durante il debug è una copia separata da quella aperta nella finestra di progettazione. Per Visual Basic la copia di output viene memorizzata nella directory \\bin, mentre per C\# nella directory \\bin\\debug.  
  
 Per attivare la sicurezza nella copia del documento aperto nella finestra di progettazione, chiudere il progetto in Visual Studio, aprire la copia del documento presente nella directory del progetto e attivare la sicurezza.  
  
## Attivazione della sicurezza dei documenti di Word durante la compilazione  
 Visual Studio attiva la sicurezza dei documenti e dei modelli di Word durante il processo di compilazione. In questo modo la sicurezza risulterà attivata all'apertura del documento per il debug.  Il documento è protetto da una password vuota.  
  
 La sicurezza viene attivata durante la compilazione poiché, se l'evento <xref:Microsoft.Office.Tools.Word.Document.Startup> del documento contiene codice che potrebbe generare eccezioni o modificare il comportamento dell'applicazione, il debug di tale codice avverrà in maniera corretta.  Attivando la sicurezza dopo l'apertura del documento, non sarebbe possibile eseguire il debug del codice di inizializzazione né testarlo.  
  
## Impostazione della password  
 Visual Studio attiva automaticamente la sicurezza, ma non fornisce alcuna password per impostazione predefinita.  Per proteggere il documento tramite password, è necessario aggiungerne una prima della distribuzione della soluzione.  L'aggiunta di una password consente agli utenti autorizzati di disattivare la sicurezza dal documento. Senza password è difficile disattivare la sicurezza.  Per ulteriori informazioni sull'impostazione di una password, vedere la Guida dell'applicazione di Office specifica.  
  
## Vedere anche  
 [Procedura: Proteggere documenti e parti di documenti a livello di codice](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Cenni preliminari sul servizio Information Rights Management e sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Sicurezza tramite password di documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Procedura: supportare l'esecuzione di codice sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  