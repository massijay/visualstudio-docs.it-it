---
title: "DA0012: Utilizzo elevato della reflection | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAReflection"
  - "vs.performance.12"
  - "vs.performance.rules.DA0012"
  - "vs.performance.DA0011"
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# DA0012: Utilizzo elevato della reflection
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0012|  
|Categoria|Utilizzo di .NET Framework|  
|Metodi di profilatura|Campionamento|  
|Messaggio|È possibile che si stia utilizzando la reflection in modo eccessivo.  L'operazione è dispendiosa.|  
|Tipo regola|Avviso|  
  
## Causa  
 Le chiamate ai metodi System.Reflection, ad esempio InvokeMember e GetMember, o ai metodi Type, ad esempio MemberInvoke, costituiscono una percentuale significativa dei dati di profilatura.  Quando è possibile, considerare la possibilità di sostituire questi metodi con associazione anticipata ai metodi di assembly dipendenti.  
  
## Descrizione della regola  
 La reflection è una funzionalità flessibile di .NET Framework che può essere utilizzata per eseguire l'associazione tardiva dell'applicazione a un Assembly di runtime dipendente oppure per creare ed eseguire dinamicamente nuovi tipi durante il runtime.  Tuttavia, queste tecniche possono ridurre le prestazioni se vengono utilizzate frequentemente o chiamate in cicli ridotti.  
  
 Per ulteriori informazioni, vedere la sezione [Reflection e associazione tardiva](http://go.microsoft.com/fwlink/?LinkId=177826) \(la pagina potrebbe essere in inglese\) del Capitolo 5 "Come migliorare le prestazioni del codice gestito" nel volume "Come migliorare prestazioni e scalabilità delle applicazioni .NET" della libreria Microsoft Patterns and Practices di MSDN.  
  
## Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [Visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilatura.  Esaminare le funzioni chiamanti del metodo System.Type o System.Reflection per trovare le sezioni del programma che fanno maggior uso delle API Reflection di .NET.  Evitare di utilizzare metodi che restituiscono metadati.  Quando le prestazioni dell'applicazione sono di importanza fondamentale potrebbe essere necessario evitare l'utilizzo dell'associazione tardiva e la creazione dinamica di tipi a tempo di esecuzione.