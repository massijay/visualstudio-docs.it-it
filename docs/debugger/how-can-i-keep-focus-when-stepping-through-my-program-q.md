---
title: "Come &#232; possibile mantenere lo stato attivo quando si esegue un programma istruzione per istruzione? | Microsoft Docs"
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
  - "vs.debug.stepping"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "debug [C++], esecuzione di istruzioni"
  - "stato attivo, mantenimento"
  - "esecuzione di istruzioni, stato attivo"
  - "finestre, risoluzione dei problemi dell'attivazione"
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Come &#232; possibile mantenere lo stato attivo quando si esegue un programma istruzione per istruzione?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrizione  
 Il programma presenta un problema di attivazione delle finestre.  L'esecuzione istruzione per istruzione del programma con il debugger interferisce con la possibilità di riprodurre il problema, poiché il programma non mantiene lo stato attivo.  Esiste un metodo per evitare che questo accada?  
  
## Soluzione  
 Se si dispone di un secondo computer, ricorrere al debug remoto.  È possibile eseguire il programma sul computer remoto mentre si esegue il debugger sull'host.  Per ulteriori informazioni, vedere [How to: Select a Remote Computer](http://msdn.microsoft.com/it-it/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
## Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)