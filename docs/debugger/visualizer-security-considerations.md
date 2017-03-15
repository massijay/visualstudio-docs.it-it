---
title: "Considerazioni sulla sicurezza del visualizzatore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "sicurezza [Visual Studio], visualizzatori"
  - "visualizzatori, sicurezza"
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Considerazioni sulla sicurezza del visualizzatore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La scrittura di un visualizzatore comporta possibili rischi per la sicurezza.  Attualmente non sono noti attacchi in grado di sfruttare tali rischi, ma gli sviluppatori devono essere a conoscenza della loro esistenza e adottare misure di sicurezza adeguate come descritto in questo argomento al fine di impedire eventuali attacchi futuri.  
  
 Per i visualizzatori del debugger sono richiesti maggiori privilegi rispetto a quelli consentiti da un'applicazione parzialmente attendibile.  I visualizzatori non vengono caricati in caso di interruzione in codice con attendibilità parziale.  Per eseguire il debug tramite un visualizzatore, è necessario eseguire il codice con attendibilità totale.  
  
## Possibile componente oggetto del debug dannoso  
 I visualizzatori sono costituiti da almeno due classi, una sul lato debugger e una sull'oggetto del debug.  I visualizzatori sono spesso distribuiti in assembly distinti inseriti in speciali directory, ma possono anche essere caricati all'esterno dell'oggetto del debug.  In tali circostanze, il debugger estrae il codice dall'oggetto del debug e lo esegue al suo interno con attendibilità totale.  
  
 L'esecuzione di codice del lato oggetto del debug con attendibilità totale risulta problematica quando l'oggetto del debug non è totalmente attendibile.  Un visualizzatore che tenti di caricare un assembly con attendibilità parziale dall'oggetto del debug nel debugger verrà terminato.  
  
 Esiste tuttavia ancora una minore vulnerabilità.  Il lato oggetto del debug può essere associato a un lato debugger caricato da un'altra origine, diversa dall'oggetto del debug.  Il lato oggetto del debug può quindi indicare al lato debugger attendibile di eseguire operazioni per proprio conto.  Se la classe del lato debugger attendibile espone un meccanismo di eliminazione file, ad esempio, l'oggetto del debug ad attendibilità parziale può richiamare tale meccanismo quando l'utente ne richiama il visualizzatore.  
  
 Per ovviare a questa vulnerabilità, tenere presenti le interfacce esposte dal visualizzatore.  
  
## Vedere anche  
 [Architettura del visualizzatore](../debugger/visualizer-architecture.md)   
 [Procedura: scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)   
 [Visualizzatori](../debugger/create-custom-visualizers-of-data.md)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)