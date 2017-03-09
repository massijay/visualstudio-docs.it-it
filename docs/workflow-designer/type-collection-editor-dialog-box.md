---
title: "Finestra di dialogo Editor raccolta di tipi | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "TypeCollectionEditor.UI"
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Finestra di dialogo Editor raccolta di tipi
La finestra di dialogo **Editor raccolta di tipi** consente di aggiungere tipi noti alle attività **Send** e **Receive**.Questa finestra di dialogo viene utilizzata anche per aggiungere argomenti di tipo generico all'attività **InvokeMethod**.Quando la finestra di dialogo **Editor raccolta di tipi** viene utilizzata per aggiungere tipi noti nelle attività **Send** e **Receive**, è necessario che tali aggiunte siano univoche.Se viene aggiunto un tipo duplicato e il commit della modifica viene eseguito facendo clic su **OK**, viene restituito un messaggio di errore.Quando la finestra di dialogo **Editor raccolta di tipi** viene utilizzata per aggiungere argomenti di tipo generico nell'attività **InvokeMethod**, è consentita l'aggiunta di tipi duplicati.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../test/includes/crabout_md.md)] tipi conosciuti, vedere [Tipi conosciuti di contratto dati](../Topic/Data%20Contract%20Known%20Types.md).  
  
 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Raccolta di tipi**.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|--------------------------------------|-----------------|  
|**Elenco dei tipi**|Un elenco dei tipi che sono stati aggiunti o rimossi.|  
  
## Per visualizzare Editor raccolta di tipi  
  
#### Per visualizzare Editor raccolta di tipi per le attività Send e Receive  
  
1.  Selezionare l'attività **Send** o l'attività **Receive** nella visualizzazione Progettazione.  
  
2.  Premere **F4** per visualizzare la finestra **Proprietà**.  
  
3.  Nella finestra **Proprietà** fare clic sul pulsante con i puntini di sospensione accanto alla proprietà **KnownTypes**.  
  
#### Per visualizzare Editor raccolta di tipi per l'attività InvokeMethod  
  
1.  Selezionare l'attività **InvokeMethod** nella visualizzazione Progettazione.  
  
2.  Premere **F4** per visualizzare la finestra **Proprietà**.  
  
3.  Nella finestra **Proprietà** fare clic sul pulsante con i puntini di sospensione accanto alla proprietà **GenericTypeArguments**.