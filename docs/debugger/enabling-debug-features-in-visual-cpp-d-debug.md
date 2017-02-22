---
title: "Attivazione delle funzionalit&#224; di debug in Visual C++ (/D_DEBUG) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/D_DEBUG (opzione del compilatore) [C++]"
  - "_DEBUG (macro)"
  - "asserzioni, attivazione di funzionalità di debug"
  - "D_DEBUG (opzione del compilatore)"
  - "compilazioni di debug, MFC"
  - "debug [C++], attivazione di funzionalità di debug"
  - "debug [MFC], attivazione di funzionalità di debug"
  - "MFC (librerie), versione di debug"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Attivazione delle funzionalit&#224; di debug in Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] le funzionalità di debug, ad esempio le asserzioni, vengono attivate quando si compila il programma definendo il simbolo **\_DEBUG**.  Il simbolo **\_DEBUG** può essere definito in uno dei due modi seguenti:  
  
-   Specificare **\#define \_DEBUG** nel codice sorgente.  
  
-   Specificare l'opzione del compilatore **\/D\_DEBUG**. Quando si crea un progetto mediante le procedure guidate di Visual Studio, il simbolo **\/D\_DEBUG** viene definito automaticamente nella configurazione di debug.  
  
 Quando viene definito **\_DEBUG**, il compilatore compila le sezioni del codice precedute e seguite da **\#ifdef \_DEBUG** e `#endif`.  
  
 La configurazione di debug di un programma MFC deve essere collegata a una versione di debug della libreria MFC.  I file di intestazione MFC determinano la versione corretta della libreria MFC con cui effettuare il collegamento in base ai simboli definiti, ad esempio **\_DEBUG** e **\_UNICODE**.  Per informazioni dettagliate, vedere [Versioni delle librerie MFC](/visual-cpp/mfc/mfc-library-versions).  
  
## Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)