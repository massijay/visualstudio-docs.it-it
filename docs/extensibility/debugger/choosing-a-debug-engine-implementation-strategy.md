---
title: "Scelta di una strategia di implementazione del motore di Debug | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motori di debug, strategie di implementazione"
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Scelta di una strategia di implementazione del motore di Debug
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilizzare l'architettura di runtime per determinare la strategia \(DE\) di implementazione del motore di debug.  Il motore di debug può essere in\-process creato il programma da sottoporre a debug, in\-process gestione \(SDM\) di debug della sessione di Visual Studio, o out\-of\-process a entrambi.  Le linee guida seguenti devono consentire di scegliere tra queste tre strategie.  
  
## Indicazioni  
 Mentre è possibile che il DE sia out\-of\-process sia per lo SDM che il programma da sottoporre a debug, non è in genere motivo a tale scopo.  Le chiamate fra i limiti dei processi sono relativamente lente.  
  
 I motori di debug sono già disponibili per l'ambiente di runtime nativi Win32 e per l'ambiente di Common Language Runtime.  Se è necessario sostituire il DE per uno di questi ambienti, è necessario creare il DE in\-process con lo SDM.  
  
 In caso contrario, si può scegliere di creare il DE in\-process a SDM o in\-process al programma da sottoporre a debug.  È importante considerare se l'analizzatore di espressioni di DE abbia bisogno di frequente accesso all'archivio simboli del programma e se l'archivio simboli può essere caricato in memoria per l'accesso rapido.  Anche considerare quanto segue:  
  
-   Se non sono molte chiamate tra l'analizzatore di espressioni e l'archivio simboli, o se l'archivio simboli può essere letto nello spazio di memoria di SDM, creare il DE in\-process a SDM.  È necessario restituire il CLSID del motore di debug a SDM nella connessione al programma.  Lo SDM utilizza questo CLSID per creare un'istanza in\-process di DE.  
  
-   Se il DE deve chiamare il programma per accedere all'archivio simboli, creare il DE in\-process con il programma.  In questo caso, il programma crea l'istanza di DE.  
  
## Vedere anche  
 [Estensibilità del Debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)