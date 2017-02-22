---
title: "Opzioni utente della soluzione (. File suo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "file. suo, package VS"
  - "file suo, package VS"
  - "soluzioni, i file con estensione suo"
  - "soluzioni, opzioni utente"
  - "file di soluzione user options (con estensione suo)"
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Opzioni utente della soluzione (. File suo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il file della soluzione utente opzioni \(Options\) contiene le opzioni di soluzione per utente. Questo file non deve essere archiviato nel controllo del codice sorgente.  
  
 Il file della soluzione utente opzioni \(Options\) è un'archiviazione strutturata o composta, file archiviati in un formato binario. Salvare informazioni utente in flussi con il nome del flusso è la chiave che verrà utilizzata per identificare le informazioni nel file con estensione suo. Il file delle opzioni utente soluzione viene utilizzato per archiviare le impostazioni delle preferenze utente e viene creato automaticamente quando Visual Studio salva una soluzione.  
  
 Quando l'ambiente viene aperto un file con estensione suo, enumera i package VS attualmente caricato. Se un VSPackage implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaccia, quindi chiama l'ambiente di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> metodo VSPackage cui viene richiesto di caricare tutti i dati dal file con estensione suo.  
  
 È responsabilità del VSPackage sapere cosa streaming potrebbero essere state scritte nel file con estensione suo. Per ogni flusso che è stato scritto, VSPackage richiama l'ambiente tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> per caricare un flusso specifico identificato dalla chiave, ovvero il nome del flusso. L'ambiente quindi richiama il VSPackage leggere tale flusso specifico passando il nome del flusso e un `IStream` puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metodo.  
  
 A questo punto, in cui viene effettuata un'altra chiamata a `LoadUserOptions` per verificare se esiste un'altra sezione del file con estensione suo che deve essere letto. Questo processo continua finché tutti i flussi di dati nel file con estensione suo sono stati letti ed elaborati dall'ambiente di.  
  
 Quando la soluzione è salvata o chiuso, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> con un puntatore al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metodo. Un `IStream` contenente le informazioni da salvare binario viene passato per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> metodo, che quindi scrive le informazioni per il file con estensione suo e chiama il `SaveUserOptions` metodo nuovamente per verificare se esiste un altro flusso di informazioni da scrivere nel file con estensione suo.  
  
 Questi due metodi, `SaveUserOptions` e `WriteUserOptions`, vengono chiamati in modo ricorsivo per ogni flusso di informazioni da salvare nel file con estensione suo, passando il puntatore a `IVsSolutionPersistence`. Tali metodi vengono chiamati in modo ricorsivo per consentire la scrittura di più flussi per il file con estensione suo. In questo modo, le informazioni utente sono persistente con la soluzione e vengano garantite che sia presente alla successiva apertura della soluzione.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Soluzioni](../../extensibility/internals/solutions.md)