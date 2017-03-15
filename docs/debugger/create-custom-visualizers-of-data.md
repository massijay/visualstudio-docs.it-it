---
title: "Visualizzatori | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.visualizer.troubleshoot"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, visualizzatori"
  - "visualizzatori"
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Visualizzatori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I visualizzatori sono componenti dell'interfaccia utente del debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Un *visualizzatore* crea una finestra di dialogo o un'altra interfaccia per visualizzare una variabile o un oggetto in modo appropriato al relativo tipo di dati.  Ad esempio, un visualizzatore HTML interpreta una stringa HTML e visualizza il risultato come apparirebbe in una finestra del browser; un visualizzatore di bitmap interpreta una struttura di bitmap e visualizza l'oggetto grafico da essa rappresentato.  Alcuni visualizzatori consentono inoltre di modificare i dati.  
  
 Il debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] include sei visualizzatori standard.  I visualizzatori di testo, HTML, XML e JSON, che possono essere usati per oggetti stringa; il visualizzatore dell'albero di WPF, per la visualizzazione delle proprietà dell'albero visuale di un oggetto WPF; e il visualizzatore di dataset, che può essere usato per oggetti DataSet, DataView e DataTable.  In futuro è possibile che Microsoft Corporation renda disponibili ulteriori visualizzatori per il download, mentre altri potranno essere disponibili tramite terze parti e dalla community.  È inoltre possibile scrivere visualizzatori personalizzati e installarli nel debugger di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
> [!NOTE]
>  Nelle app di **Store** sono supportati solo i visualizzatori di testo standard, HTML, XML e JSON.  Non sono supportati i visualizzatori personalizzati \(creati dall'utente\).  
  
 Nel debugger i visualizzatori sono rappresentati da un'icona a forma di lente di ingrandimento.  Quando si nota l'icona a forma di lente di ingrandimento all'interno di un **Suggerimento dati**, nella finestra delle variabili del debugger o nella finestra di dialogo **Controllo immediato**, è possibile fare clic su di essa per selezionare un visualizzatore appropriato per il tipo di dati dell'oggetto corrispondente.  
  
 I visualizzatori non sono supportati in Compact Framework.  
  
> [!NOTE]
>  Per i visualizzatori del debugger sono richiesti maggiori privilegi rispetto a quelli consentiti da un'applicazione parzialmente attendibile.  Di conseguenza, i visualizzatori non vengono caricati in caso di interruzione in codice con attendibilità parziale.  Per eseguire il debug tramite un visualizzatore, è necessario eseguire il codice con attendibilità totale.  
  
## In questa sezione  
 [Procedura: scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)  
  
 [Procedura dettagliata: scrittura di un visualizzatore in C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)  
  
 [Procedura: testare un visualizzatore ed eseguirne il debug](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Informazioni di riferimento sulle API del visualizzatore](../debugger/visualizer-api-reference.md)  
  
## Sezioni correlate  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)