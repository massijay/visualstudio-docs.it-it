---
title: "Scheda Messaggi, Finestra di dialogo Opzioni messaggio | Microsoft Docs"
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
  - "opzioni messaggio, Messaggi"
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Scheda Messaggi, Finestra di dialogo Opzioni messaggio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare la scheda **Messaggi** per selezionare quali tipi di messaggio elencare in [Visualizzazione messaggi](../debugger/messages-view.md) e per specificare i criteri di ricerca del messaggio.  Per visualizzare la [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md), scegliere **Registra messaggi** dal menu **Spy**.  
  
 In genere prima si seleziona **Gruppi di messaggi**, quindi si ottimizza la selezione scegliendo **Messaggi da visualizzare**.  Il pulsante **Tutti** consente di selezionare tutti i tipi di messaggio mentre il pulsante **Nessuno** consente di deselezionare tutti i tipi.  
  
 Nella scheda **Messaggi** sono disponibili le impostazioni seguenti:  
  
 **Messaggi da visualizzare**  
 Consente di selezionare messaggi specifici da visualizzare.  Quando si crea una nuova finestra Messaggi, è possibile visualizzare tutti i messaggi.  Quando si filtrano messaggi dalla scheda **Messaggi**, quel filtro viene applicato solo ai nuovi messaggi e non a quelli che sono già stati visualizzati nella visualizzazione delle finestre.  
  
 **Gruppi di messaggi**  
 Consente di selezionare i gruppi di messaggi da visualizzare.  I gruppi disponibili includono:  
  
-   WM\_USER: con un codice maggiore o uguale a WM\_USER  
  
-   Registrato: registrato con la chiamata **RegisterWindowMessage**  
  
-   Sconosciuto: messaggi sconosciuti nell'intervallo compreso tra 0 e \(WM\_USER – 1\)  
  
 Notare che questi **Gruppi di messaggi** non sono mappati alle voci specifiche sotto **Messaggi da visualizzare**.  Quando si seleziona un gruppo, la selezione è applicata direttamente al flusso di messaggi.  
  
 Una casella di controllo disabilitata all'interno di **Gruppi di messaggi** indica che la casella di riepilogo **Messaggi da visualizzare** è stata modificata relativamente ai messaggi di quel gruppo. Non tutti i tipi di messaggio di quel gruppo vengono selezionati.  
  
 **Salva impostazioni come predefinite**  
 Consente di salvare le impostazioni correnti per un uso successivo come opzioni di ricerca del messaggio.  Queste impostazioni vengono salvate anche alla chiusura di Spy\+\+.