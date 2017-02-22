---
title: "Eliminazione di ~ SAK file | Microsoft Docs"
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
  - "file temporanei"
  - "~ sak file"
  - "origine plug-in del controllo, ~ file SAK"
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Eliminazione di ~ SAK file
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In plug\-in controllo del codice sorgente l'API 1,2, i file di ~SAK sono stati sostituiti dai flag di funzionalità e le nuove funzioni che rilevano se un plug\-in controllo del codice sorgente supporta il file di MSSCCPRJ e estrazioni in modo condivisi.  
  
## file di ~SAK  
 Visual Studio .NET 2003. sono stati creati i file temporanei con prefisso ~SAK.  Questi file vengono utilizzati per determinare se un plug\-in controllo del codice sorgente supporta:  
  
-   il file di MSSCCPRJ.SCC.  
  
-   Completamenti della transazione \(condivisi\) più.  
  
 Per i collegamenti che supportano le funzioni avanzate forniti nel plug\-in controllo del codice sorgente l'API 1,2, l'ide per rilevare queste funzionalità senza creare i file temporanei con l'utilizzo delle nuove funzionalità, flag e funzioni, dettagliate nelle sezioni seguenti.  
  
## nuovi flag di funzionalità  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## nuove funzioni  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Se un plug\-in controllo del codice sorgente supporta i completamenti della transazione \(condivisi\) più, quindi dichiarare la funzionalità di `SCC_CAP_MULTICHECKOUT` e implementa la funzione di `SccIsMultiCheckOutEnabled` .  Questa funzione viene chiamata ogni volta che un'operazione di completamento della transazione viene applicata a qualsiasi progetto incluso nel controllo del codice sorgente.  
  
 Se un plug\-in controllo del codice sorgente supporta la creazione e l'utilizzo di un file di MSSCCPRJ.SCC, quindi dichiarare la funzionalità di `SCC_CAP_SCCFILE` e implementa [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md).  Questa funzione viene chiamata con un elenco di file.  La funzione restituisce `TRUE/FALSE` per ciascun file di indicare se Visual Studio è necessario utilizzare un file di MSSCCPRJ.SCC per.  Se il plug\-in controllo del codice sorgente sceglie di non supportare queste nuove funzionalità e funzioni, può utilizzare la seguente chiave del Registro di sistema per disabilitare la creazione di questi file:  
  
 \[\=dword HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateTemporaryFilesInSourceControl ": 00000001  
  
> [!NOTE]
>  Se questa chiave del Registro di sistema è impostata su dword: 00000000, è equivalente alla chiave che è inesistente e Visual Studio è ancora tenta di creare file temporanei.  Tuttavia, se la chiave del Registro di sistema è impostata su dword: 00000001, Visual Studio non tenta di creare file temporanei.  Anziché presuppone che il plug\-in controllo del codice sorgente non supporti il file di MSSCCPRJ.SCC e non supporti i completamenti della transazione condivisi.  
  
## Vedere anche  
 [Novità di origine controllo plug\-in API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)