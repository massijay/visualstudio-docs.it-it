---
title: "Strumenti personalizzati | Microsoft Docs"
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
  - "Package VS, gli strumenti personalizzati"
  - "strumenti [Visual Studio], personalizzati"
  - "strumenti personalizzati"
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Strumenti personalizzati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

*Gli strumenti personalizzati* consentono di associare uno strumento con un elemento in un progetto ed eseguire questo strumento ogni volta che il file viene salvato.  Alcuni strumenti personalizzati, talvolta noti come *generatori di file singoli*, vengono spesso utilizzati per implementare i traduttori che generano il codice dai dati e viceversa.  Ad esempio, i generatori di file singoli creano [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e il codice sorgente di[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] da file RESX e settings.  Il codice sorgente generato fornisce accesso fortemente tipizzato ai dati dei file RESX e settings.  I tipi di progetto di[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e di [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] supportano gli strumenti personalizzati, i tipi di progetto di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] no.  Altri tipi di progetto può inoltre supportare gli strumenti personalizzati.  
  
 gli strumenti personalizzati sono componenti registrate che implementano l'interfaccia di `IVsSingleFileGenerator` .  
  
 Gli strumenti personalizzati sono associati a un oggetto interfaccia di `ProjectItem` e sono simili a finestre di progettazione ed editor.  Uno strumento personalizzato acquisisce il file rappresentato da `ProjectItem` come input e produce un nuovo file il cui nome file viene fornito con il metodo di `DefaultExtension` .  
  
## In questa sezione  
 [Implementazione di generatori di File singolo](../../extensibility/internals/implementing-single-file-generators.md)  
 Viene descritto come utilizzare l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> per implementare uno strumento personalizzato.  
  
 [Determinazione dello spazio dei nomi predefinito di un progetto](../../misc/determining-the-default-namespace-of-a-project.md)  
 Viene descritto come determinare lo spazio dei nomi corretto in base al linguaggio utilizzato.  
  
 [Registrazione di generatori di File singolo](../../extensibility/internals/registering-single-file-generators.md)  
 Fornisce descrizioni per tutte le voci del Registro di sistema per uno strumento personalizzato.  
  
 [Esposizione di tipi di finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Viene illustrato come i sistemi di progetto fornisce supporto per le finestre di progettazione visiva alle classi e ai tipi generati accesso ai file eseguibili portabili temporanei \(PE\).  
  
 [Salvare in modo permanente la proprietà di un elemento di progetto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Viene illustrato come salvare in modo permanente una proprietà dell'elemento di progetto, l'autore di un file di origine, nel file di progetto.  
  
## Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Vengono fornite informazioni dettagliate su <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, che trasforma un file a un input in un file di output che può essere compilato o aggiungere a un progetto.  
  
 <xref:EnvDTE.ProjectItem>  
 Viene illustrata l'interfaccia di `ProjectItem` , che rappresenta un elemento in un progetto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Vengono fornite informazioni dettagliate sul metodo di `DefaultExtension` , che recupera l'estensione di file che è fornita al nome file di output.  
  
## Sezioni correlate  
 [Estensione di progetti](../../extensibility/extending-projects.md)  
 Viene descritto come utilizzare i progetti e le soluzioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] organizzare i file di codice e i file di risorse e come implementare il controllo del codice sorgente.