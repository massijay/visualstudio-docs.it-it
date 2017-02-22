---
title: "DA0004: Utilizzo elevato del processore | Microsoft Docs"
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
  - "vs.performance.rules.DAHighProcessorUsage"
  - "vs.performance.rules.DA0004"
  - "vs.performance.DA0004"
  - "vs.performance.4"
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0004: Utilizzo elevato del processore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0004|  
|Category|Utilizzo di strumenti di profilatura|  
|Metodi di profilatura|Strumentazione<br /><br /> Campionamento|  
|Messaggio|L'utilizzo del processore è costantemente superiore al 75%.  Si consiglia di utilizzare la modalità campionamento per le applicazioni basate sulla CPU.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## Causa  
 L'utilizzo del processore \(CPU\) è significativamente elevato nei dati di profilatura raccolti utilizzando il metodo di strumentazione.  Considerare l'utilizzo del metodo di profilatura del campionamento per profilare applicazioni associate alla CPU.  
  
## Descrizione della regola  
 Durante l'esecuzione di questo profilo, il processore o i processori sono stati molto occupati in modo coerente.  Un elevato utilizzo della CPU elevato può indicare un'applicazione basata sulla CPU.  In genere i profili instrumentati non rappresentano il modo più valido per esaminare gli scenari di utilizzo della CPU.  Il campionamento di solito è più efficace quando si profilano applicazioni che per la maggior parte del tempo eseguono istruzioni sul processore.  
  
## Come correggere le violazioni  
 Tranne nei casi in cui si richiedano intervalli di funzioni o si sia interessati più a comprendere l'input\/output che i colli di bottiglia del processore, considerare una nuova esecuzione del profilo dell'applicazione tramite il metodo di campionamento anziché il metodo di strumentazione.