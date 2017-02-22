---
title: "Scheda Classe, finestra di dialogo Propriet&#224; finestra | Microsoft Docs"
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
  - "Finestra di dialogo Proprietà finestra, scheda Classe"
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Scheda Classe, finestra di dialogo Propriet&#224; finestra
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare la scheda **Classe** per visualizzare informazioni sulla classe della finestra selezionata.  Per visualizzare la [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo sulla finestra [Visualizzazione finestre](../debugger/windows-view.md).  Selezionare un nodo qualsiasi della finestra nella struttura ad albero, quindi scegliere **Proprietà** dal menu **Visualizza**.  
  
 Nella scheda **Classe** sono disponibili le impostazioni seguenti:  
  
|Voce|Descrizione|  
|----------|-----------------|  
|**Nome classe**|Nome \(o numero ordinale\) di questa classe della finestra.|  
|**Class Styles**|Combinazione di codici di stile della classe.|  
|**Class Bytes**|Dati specifici dell'applicazione associati a questa classe della finestra.|  
|**Class Atom**|Atomo per la classe restituita dalla chiamata **RegisterClass**.|  
|**Instance Handle**|Handle di istanza del modulo che ha registrato la classe.  Gli handle dell'istanza non sono univoci.|  
|**Window Bytes**|Numero di byte aggiuntivi associati a ogni finestra di questa classe.  Il significato di questi byte è determinato dall'applicazione.  Espandere la casella di riepilogo per visualizzare i valori dei byte in formato DWORD.|  
|**Window Proc**|Indirizzo corrente della funzione **WndProc** per le finestre di questa classe.  Differisce da **Window Proc** della scheda **Generale** se la finestra è impostata come sottoclasse.|  
|**Menu Name**|Nome del menu principale associato alle finestre di questa classe \("none" se non è presente alcun menu\).|  
|**Icon Handle**|Handle per l'icona associata alle finestre di questa classe \("none" se non è presente alcuna icona\).|  
|**Cursor Handle**|Handle per il cursore associato alle finestre di questa classe \("none" se non è presente alcun cursore\).|  
|**Bkgnd Brush**|Handle per il pennello di sfondo associato alle finestre di questa classe oppure uno dei colori predefiniti COLOR\_ \* per colorare lo sfondo della finestra \("none" se non è presente alcun pennello\).|