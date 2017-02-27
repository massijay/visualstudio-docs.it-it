---
title: "Scheda Generale, finestra di dialogo Propriet&#224; finestra | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Finestra di dialogo Proprietà finestra, scheda Generale"
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Scheda Generale, finestra di dialogo Propriet&#224; finestra
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare la scheda **Generale** per visualizzare informazioni sulla finestra selezionata.  Per visualizzare la [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo sulla finestra [Visualizzazione finestre](../debugger/windows-view.md).  Selezionare un nodo qualsiasi della finestra nella struttura ad albero, quindi scegliere **Proprietà** dal menu **Visualizza**.  
  
 Nella scheda **Generale** sono disponibili le impostazioni seguenti:  
  
|Voce|Descrizione|  
|----------|-----------------|  
|**Window Caption**|Testo nel titolo della finestra o testo contenuto in una finestra se si tratta di un controllo.|  
|**Window Handle**|ID univoco di questa finestra.  I numeri di handle della finestra vengono riutilizzati e pertanto identificano una finestra solo per la relativa durata.|  
|**Window Proc**|Indirizzo virtuale della funzione routine di finestra per questa finestra.  Questo campo specifica inoltre se si tratta di una finestra Unicode e se è impostata come sottoclasse.|  
|**Rectangle**|Rettangolo delimitatore della finestra.  Vengono visualizzate anche le dimensioni del rettangolo.  Le unità sono espresse in pixel rispetto alle coordinate dello schermo.|  
|**Restored Rect**|Rettangolo delimitatore della finestra ripristinata.  Vengono visualizzate anche le dimensioni del rettangolo.  Le impostazioni Restored Rect e Rectangle differiscono solo quando la finestra viene ingrandita o ridotta.  Le unità sono espresse in pixel rispetto alle coordinate dello schermo.|  
|**Client Rect**|Rettangolo delimitatore dell'area client della finestra.  Vengono visualizzate anche le dimensioni del rettangolo.  Le unità sono espresse in pixel relativamente alla parte superiore sinistra dell'area client della finestra.|  
|**Instance Handle**|Handle dell'istanza dell'applicazione.  Gli handle dell'istanza non sono univoci.|  
|**Control ID o Menu Handle**|Se la finestra visualizzata è una finestra figlio, viene visualizzata l'etichetta Control ID,  ossia un numero intero che identifica l'ID controllo di tale finestra figlio.  Se la finestra visualizzata non è una finestra figlio, viene visualizzata l'etichetta Menu Handle,  ossia un numero intero che identifica l'handle del menu associato a tale finestra.|  
|**User Data**|Dati specifici dell'applicazione associati a questa struttura della finestra.|  
|**Window Bytes**|Numero di byte aggiuntivi associati a questa finestra.  Il significato di questi byte è determinato dall'applicazione.  Espandere la casella di riepilogo per visualizzare i valori dei byte in formato DWORD.|