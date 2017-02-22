---
title: "Implementazione di generatori di File singolo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti personalizzati, implementazione"
  - "progetti [Visual Studio SDK], estendibilità"
  - "progetti [Visual Studio SDK], gestito strumenti personalizzati"
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementazione di generatori di File singolo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Uno strumento personalizzato \(talvolta definita generatore di file singolo \)può essere utilizzato per estendere [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i sistemi di progetto csprcs in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Uno strumento personalizzato è un componente COM che implementa l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  L'utilizzo di questa interfaccia, uno strumento personalizzato trasforma un file a un input in un file di output.  Il risultato della trasformazione può essere codice sorgente, o qualsiasi altro output che è utile.  Due esempi dei file di codice strumento\-generati personalizzati sono codice generato in seguito a modifiche in una finestra di progettazione visiva e file compilati utilizzando il Web Services Description Language \(WSDL\)\).  
  
 Quando uno strumento personalizzato viene caricato, o il file di input viene salvato, attraverso il sistema di progetto chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> e passa un riferimento a un'interfaccia di callback di <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> , con cui lo strumento può segnalare lo stato dell'utente.  
  
 Il file di output che lo strumento personalizzato generato viene aggiunto al progetto con una dipendenza riguardanti l'archivio di input.  Il sistema del progetto determina automaticamente il nome del file di output, in base alla stringa restituita dall'implementazione personalizzata dello strumento di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 uno strumento personalizzato deve implementare l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  Facoltativamente, gli strumenti personalizzati supportano l'interfaccia di <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> per recuperare informazioni da origini diverse da di input.  Tuttavia, prima di poter utilizzare uno strumento personalizzato, è necessario registrarlo con il sistema o in locale il Registro di sistema di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Per ulteriori informazioni sulla registrazione degli strumenti personalizzati, vedere [Registrazione di generatori di File singolo](../../extensibility/internals/registering-single-file-generators.md).  
  
## Vedere anche  
 [Determinazione dello spazio dei nomi predefinito di un progetto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Esposizione di tipi di finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)