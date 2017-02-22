---
title: "Raccolta di dati di interazione tra livelli mediante l&#39;IDE di Visual Studio | Microsoft Docs"
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
  - "vs.performance.property.tierinteraction"
helpviewer_keywords: 
  - "strumenti per la profilatura, profilatura ADO.NET"
  - "metodo di profilatura di interazione tra livelli"
  - "strumenti per la profilatura, metodo di interazione tra livelli"
  - "ADO.NET (profilatura delle prestazioni)"
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Raccolta di dati di interazione tra livelli mediante l&#39;IDE di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il profilo delle interazioni tra livelli offre informazioni aggiuntive sui tempi di esecuzione delle funzioni di applicazioni multilivello che comunicano con database tramite i servizi ADO.NET.  I dati vengono raccolti solo per chiamate di funzione sincrone.  
  
 **Versioni di Visual Studio**  
  
 I dati di profilatura dell'interazione tra livelli possono essere raccolti tramite Visual Studio Ultimate, Visual Studio Premium o Visual Studio Professional.  Tuttavia, i dati di profilatura dell'interazione tra livelli possono essere visualizzati solo in VS Ultimate e VS Premium.  
  
 **Windows 8 e Windows Server 2012**  
  
 Per raccogliere dati di interazione tra livelli nelle applicazioni desktop di Windows 8 e nelle applicazioni Windows Server 2012, è necessario utilizzare il metodo di strumentazione.  Non è possibile raccogliere dati di interazione tra livelli per le applicazioni Windows Store.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  È possibile includere i dati di interazione tra livelli in tutti i metodi di profilatura su un'altra versione di Windows supportata.  
  
 **Creazione guidata sessione di prestazioni**  
  
 A causa di un bug nella Creazione guidata sessione di prestazioni, è necessario aggiungere l'opzione di raccolta dati di interazione tra livelli ad un'esecuzione di profilatura da Esplora Prestazioni.  È inoltre necessario aggiungere il progetto, il file eseguibile, o il sito Web al nodo di destinazione di Esplora prestazioni.  
  
### Per aggiungere dati di interazione tra livelli a un'esecuzione della profilatura tramite pagine delle proprietà della sessione di prestazioni  
  
1.  In Esplora Prestazioni, scegliere **Proprietà** dal menu contestuale.  
  
2.  Selezionare la pagina **Interazione tra livelli**, quindi selezionare la casella di controllo **Abilita profilo interazione tra livelli**.  
  
3.  In Esplora prestazioni, selezionare il nodo **Destinazioni**, quindi specificare il progetto, il file eseguibile o il sito Web che si desidera profilare.  
  
## Vedere anche  
 [Visualizzazione Interazioni tra livelli](../profiling/tier-interactions-view.md)