---
title: "Scheda Finestre, finestra di dialogo Propriet&#224; finestra | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Finestra di dialogo Proprietà finestra, scheda Finestre"
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Scheda Finestre, finestra di dialogo Propriet&#224; finestra
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare la scheda **Finestre** per visualizzare informazioni sulle finestre correlate alla finestra selezionata.  Per visualizzare la [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo sulla finestra [Visualizzazione finestre](../debugger/windows-view.md).  Selezionare un nodo qualsiasi della finestra nella struttura ad albero, quindi scegliere **Proprietà** dal menu **Visualizza**.  
  
 Nella scheda **Finestre** sono disponibili le impostazioni seguenti:  
  
|Voce|Descrizione|  
|----------|-----------------|  
|**Next Window**|Handle della finestra successiva di pari livello nella stessa sequenza \(ordine z\) indicata nella visualizzazione struttura ad albero della finestra \("none" se non è disponibile alcuna finestra successiva\).  Scegliere questa voce per visualizzare le proprietà della finestra successiva.|  
|**Previous Window**|Handle della finestra precedente di pari livello nella stessa sequenza \(ordine z\) indicata nella visualizzazione struttura ad albero della finestra \("none" se non è disponibile alcuna finestra precedente\).  Scegliere questa voce per visualizzare le proprietà della finestra precedente.|  
|**Parent Window**|Handle della finestra padre di questa finestra \("none" se non è disponibile alcuna finestra padre\).  Scegliere questa voce per visualizzare le proprietà della finestra padre.|  
|**First Child**|Handle della prima finestra figlio di questa finestra nella sequenza \(ordine z\) indicata nella visualizzazione struttura ad albero della finestra \("none" se non sono disponibili finestre figlio\).  Scegliere questo valore per visualizzare le proprietà della prima finestra figlio.|  
|**Owner Window**|Handle della finestra proprietaria di questa finestra.  Le finestre di dialogo modali di sistema, ad esempio, appartengono in genere alla finestra principale di un'applicazione \("none" se non è presente alcun elemento proprietario\).  Scegliere questa voce per visualizzare le proprietà della finestra proprietaria.|