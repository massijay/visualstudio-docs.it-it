---
title: "Componente aggiuntivo di Excel di esempio per i test codificati dell&#39;interfaccia utente | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "test codificati dell'interfaccia utente, componente aggiuntivo di esempio per Excel"
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "mlearned"
manager: "douge"
---
# Componente aggiuntivo di Excel di esempio per i test codificati dell&#39;interfaccia utente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo componente aggiuntivo di esempio per [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] è specificamente progettato per supportare i test codificati dell'interfaccia utente dei fogli di lavoro di Excel registrati ed eseguiti in Visual Studio Enterprise. Per creare il componente aggiuntivo, si usa Visual Studio Tools per Office.  
  
 Per altre informazioni su come creare un componente aggiuntivo di Excel, vedere [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md) o cercare "componente aggiuntivo Excel" in MSDN.  
  
 Anche se il componente aggiuntivo per Excel non è l'argomento principale di questi documenti sull'estensione dei test codificati dell'interfaccia utente per Excel, alcuni commenti possono essere utili.  
  
 Parti importanti di questo componente aggiuntivo:  
  
-   Classe `ThisAddIn`: gestisce il canale Servizi remoti .NET tra `ExcelUICommunicator` e l'[Estensione di esempio per i test codificati dell'interfaccia utente per Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx` : certificato di sicurezza per il test del componente aggiuntivo.  
  
-   Classe `ExcelUICommunicator`: questa classe implementa l'interfaccia `IExcelUICommunication`.  
  
## Classe ThisAddIn  
 La maggior parte degli elementi di questa classe viene effettivamente generata da Visual Studio Tools per Office nel file `ThisAddIn.Designer.cs` quando si crea il progetto Componente aggiuntivo di Excel.  
  
 I membri che è necessario implementare sono i gestori eventi: `ThisAddIn_Startup()` e `ThisAddIn_Shutdown()`,  il cui scopo è inizializzare o chiudere il canale Servizi remoti .NET usato da `ExcelUICommunicator`.  
  
## ExcelCodedUIAddinHelper\_TemporaryKey.pfx  
 Questo file contiene un certificato di sicurezza temporaneo che viene generato da Visual Studio Tools per Office e concede all'assembly del componente aggiuntivo l'autorizzazione per operare nel processo di Excel per il test del componente aggiuntivo e dell'estensione.  È consigliabile eliminare questo certificato e crearne uno nuovo nella scheda **Firma** della finestra **Proprietà** del progetto o associare il proprio certificato di test.  
  
## Classe ExcelUICommunicator  
 Questa classe implementa l'interfaccia `IExcelUITestCommunication` e ottiene dal modello a oggetti di Excel le informazioni dell'interfaccia utente richieste.  Per altre informazioni, vedere [Interfaccia Excel Communicator di esempio](../test/sample-excel-communicator-interface.md).  
  
## Vedere anche  
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md)   
 [Office and SharePoint Development](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)