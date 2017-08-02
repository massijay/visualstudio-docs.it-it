---
title: "Procedura: associare estensioni di codice gestito a documenti"
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
  - "documenti [sviluppo per Office in Visual Studio], estensioni di codice gestito"
  - "estensioni di codice gestito [sviluppo per Office in Visual Studio], collegamento"
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Procedura: associare estensioni di codice gestito a documenti
  È possibile associare un assembly di personalizzazione a un documento di Microsoft Office Word o a una cartella di lavoro di Microsoft Office Excel esistenti.  Il documento o la cartella di lavoro può avere un formato di file supportati da progetti e dagli strumenti di sviluppo di Microsoft Office in Visual Studio.  Per ulteriori informazioni, vedere [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Per associare una personalizzazione a un documento di Word o Excel, utilizzare il metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> della classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  Poiché la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> è progettata per essere eseguita in un computer in cui non è installato Microsoft Office, è possibile utilizzare questo metodo nelle soluzioni non direttamente correlate allo sviluppo Microsoft Office, ad esempio un'applicazione console o Windows Form.  
  
> [!NOTE]  
>  Non sarà possibile caricare la personalizzazione se il codice prevede la presenza di controlli di cui il documento specificato è privo.  
  
 ![Collegamento a video](~/data-tools/media/playvideo.gif "Collegamento a video") Per una dimostrazione video correlata, vedere la [procedura relativa all'associazione o alla dissociazione di un assembly VSTO da un documento di Word](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### Per collegare le estensioni di codice gestito a un documento  
  
1.  In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto Windows Form, aggiungere un riferimento agli assembly di e Microsoft.VisualStudio.Tools.Applications.Runtime.dll Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Aggiungere l'istruzione **Imports** o **using** seguente all'inizio del file di codice.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#4)]  
  
3.  Chiamare il metodo statico <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.  
  
     Nell'esempio di codice riportato di seguito viene utilizzato l'overload <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>,  il quale assume il percorso completo del documento e un oggetto <xref:System.Uri> che specifica il percorso del manifesto di distribuzione per la personalizzazione che si desidera associare al documento.  In questo esempio si presuppone che un documento di Word denominato **WordDocument1.docx** si trovi sul desktop e che il manifesto di distribuzione sia situato in una cartella denominata **Publish** anch'essa sul desktop.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#3)]  
  
4.  Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera associare la personalizzazione.  Il computer disponga di Visual Studio 2010 tools per Office runtime installati.  
  
## Vedere anche  
 [Gestione dei documenti di un server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Procedura: rimuovere estensioni di codice gestito dai documenti](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  