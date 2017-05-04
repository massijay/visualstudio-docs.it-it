---
title: "Procedura: rimuovere estensioni di codice gestito dai documenti | Microsoft Docs"
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
  - "estensioni di codice gestito [sviluppo per Office in Visual Studio], rimozione"
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Procedura: rimuovere estensioni di codice gestito dai documenti
  È possibile rimuovere a livello di codice l'assembly di personalizzazione da un documento o da una cartella di lavoro che fa parte di una personalizzazione a livello di documento per Microsoft Office Word o Microsoft Office Excel.  Gli utenti potranno quindi aprire i documenti e visualizzarne il contenuto, ma le eventuali interfacce utente personalizzate aggiunte ai documenti non saranno visualizzate e il codice non verrà eseguito.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 È possibile rimuovere l'assembly di personalizzazione utilizzando uno dei metodi RemoveCustomization forniti dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Il metodo da utilizzare varia a seconda che si desideri rimuovere la personalizzazione in fase di esecuzione \(ovvero, eseguendo il codice nella personalizzazione quando il documento di Word o la cartella di lavoro di Excel è aperta\) o che si desideri rimuovere la personalizzazione da un documento chiuso o da un documento che si trova in un server in cui non è installato Microsoft Office.  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere la [procedura relativa all'associazione o alla dissociazione di un assembly VSTO da un documento di Word](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### Per rimuovere l'assembly di personalizzazione in fase di esecuzione  
  
1.  Nel codice della personalizzazione, chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> \(per Word\) o <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> \(per Excel\).  Questo metodo deve essere chiamato solo quando la personalizzazione non è più necessaria.  
  
     La posizione da cui si chiama questo metodo nel codice dipende dal modo in cui viene utilizzata la personalizzazione.  Ad esempio, se i clienti utilizzano le funzionalità della personalizzazione finché non sono pronti a inviare il documento ad altri clienti che richiedono unicamente il documento e non la personalizzazione, è possibile fornire un'interfaccia utente che chiami RemoveCustomization quando il cliente fa clic su di esso.  In alternativa, se la personalizzazione popola il documento con dati quando viene aperto per la prima volta, ma la personalizzazione non fornisce altre funzionalità a cui i clienti possono accedere direttamente, è possibile chiamare RemoveCustomization non appena termina l'inizializzazione del documento da parte della personalizzazione.  
  
### Per rimuovere l'assembly di personalizzazione da un documento chiuso o un documento in un server  
  
1.  In un progetto che non richiede Microsoft Office, ad esempio un'applicazione console o un progetto Windows Form, aggiungere un riferimento all'assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Aggiungere l'istruzione **Imports** o **using** seguente all'inizio del file di codice.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#1)]  
  
3.  Chiamare il metodo statico <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> della classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> e specificare il percorso del documento della soluzione per il parametro.  
  
     L'esempio di codice seguente presuppone che si stia rimuovendo la personalizzazione da un documento denominato **WordDocument1.docx** che si trova sul desktop.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#2)]  
  
4.  Compilare il progetto ed eseguire l'applicazione nel computer in cui si desidera rimuovere la personalizzazione.  Il computer disponga di Visual Studio 2010 tools per Office runtime installati.  
  
## Vedere anche  
 [Gestione dei documenti di un server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Procedura: associare estensioni di codice gestito a documenti](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  