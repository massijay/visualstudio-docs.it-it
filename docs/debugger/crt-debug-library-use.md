---
title: "Utilizzo della libreria di debug CRT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.debug.runtime"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "/DEBUG (opzione del linker) [C++]"
  - "-LDd (funzione del compilatore) [C++]"
  - "/MDd (opzione del compilatore) [C++]"
  - "/MTd (opzione del compilatore) [C++]"
  - "crtdbg.h (file)"
  - "libreria di debug"
  - "DEBUG (opzione del linker) [C++]"
  - "debug [CRT], CRT (libreria di debug)"
  - "LDd (funzione del compilatore) [C++]"
  - "librerie, CRT (libreria di debug)"
  - "MDd (opzione del compilatore) [C++]"
  - "MTd (opzione del compilatore) [C++]"
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Utilizzo della libreria di debug CRT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La libreria di runtime del linguaggio C offre un ampio supporto per il debug.  Per utilizzare una delle librerie di debug CRT, è necessario eseguire il collegamento con l'opzione [\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info) ed effettuare la compilazione con **\/MDd**, **\/MTd** o **\/LDd**.  
  
## Osservazioni  
 Le definizioni e le macro principali del debug CRT sono disponibili nel file di intestazione CRTDBG.h.  
  
 Le funzioni delle librerie di debug CRT sono compilate con informazioni di debug [\/Z7, \/Zd, \/Zi, \/ZI \(Formato informazioni di debug](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\) e senza ottimizzazione.  Alcune funzioni contengono asserzioni per la verifica di parametri ricevuti e viene fornito il codice sorgente.  Grazie a questo codice sorgente è possibile eseguire passo passo le funzioni CRT per accertarsi che funzionino correttamente e rilevare eventuali parametri o stati di memoria errati. Parte della tecnologia CRT è proprietaria e non fornisce codice sorgente per la gestione delle eccezioni, la virgola mobile e alcune altre routine.  
  
 Quando si implementa Visual C\+\+, è possibile scegliere di installare il codice sorgente della libreria di runtime del linguaggio C sul disco rigido.  Se non si installa il codice sorgente, sarà necessario il CD\-ROM per eseguire un passaggio alla volta le funzioni CRT.  
  
 Per ulteriori informazioni sulle varie librerie di runtime che è possibile utilizzare, vedere [Librerie di runtime del linguaggio C](/visual-cpp/c-runtime-library/crt-library-features).  
  
## Vedere anche  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)   
 [\/MD, \/MT, \/LD \(Utilizza la libreria di runtime\)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library)