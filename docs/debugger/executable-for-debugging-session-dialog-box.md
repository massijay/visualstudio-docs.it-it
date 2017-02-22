---
title: "Finestra di dialogo Eseguibile per la sessione di debug | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exefordebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "file eseguibili, specifica durante il debug"
  - "DLL, debug"
  - "debugger, finestra di dialogo Eseguibile per la sessione di debug"
  - "finestra di dialogo Eseguibile per la sessione di debug"
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Finestra di dialogo Eseguibile per la sessione di debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo viene visualizzata quando si tenta di eseguire il debug di una DLL per la quale non è stato specificato alcun eseguibile.  Visual Studio non è in grado di avviare direttamente una DLL,  ma avvierà l'eseguibile specificato.  È possibile eseguire il debug della DLL quando viene chiamata dall'eseguibile.  
  
 **Nome del file eseguibile**  
 Immettere il nome e il percorso di un file eseguibile che chiama la DLL sottoposta a debug.  
  
 **URL per accedere al progetto \(solo ATL Server\)**  
 Se si esegue il debug di una DLL di ATL Server, immettere l'URL del progetto.  
  
 Una volta immesse, queste impostazioni sono archiviate nelle Pagine delle proprietà del progetto, pertanto non è necessario immetterle nuovamente per le successive sessioni di debug.  Se occorre modificare queste impostazioni, aprire le Pagine delle proprietà e modificare i valori.  Per ulteriori informazioni sulla specifica di un eseguibile per la sessione di debug, vedere [Debug delle DLL](../debugger/how-to-debug-native-dlls.md).  
  
## Vedere anche  
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)