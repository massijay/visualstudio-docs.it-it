---
title: "Azioni personalizzate nelle aree di modulo di Outlook"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "azioni personalizzate [sviluppo per Office in Visual Studio]"
  - "aree di modulo [sviluppo per Office in Visual Studio], azioni personalizzate"
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Azioni personalizzate nelle aree di modulo di Outlook
  Le azioni visualizzano pulsanti che consentono agli utenti di rispondere a un elemento di Microsoft Office Outlook.  Ad esempio, per rispondere a un elemento di posta, gli utenti fanno clic sui pulsanti di azione **Rispondi**, **Rispondi a tutti** o **Inoltra**.  Ognuna di queste azioni crea un nuovo elemento di posta e popola i campi dell'elemento utilizzando informazioni dell'elemento originale.  
  
 È possibile creare un'azione personalizzata che apre qualsiasi tipo di elemento di Outlook.  Ad esempio, è possibile aggiungere un'azione personalizzata che apre un nuovo elemento appuntamento o attività.  Per popolare i campi del nuovo elemento, impostare le proprietà di un'azione personalizzata o utilizzare codice personalizzato.  Le azioni personalizzate vengono visualizzate nell'elenco a discesa **Azioni personalizzate** di un elemento aperto in una finestra di controllo Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Aggiunta di azioni personalizzate a un'area del modulo  
 Per aggiungere un'azione personalizzata a un'area del modulo, utilizzare la finestra di dialogo **Azioni personalizzate**.  È possibile aprire la finestra di dialogo **Azioni personalizzate** in **Esplora soluzioni** espandendo il nodo **Manifesto**, selezionando la proprietà **CustomActions** quindi facendo clic sul pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](~/docs/sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")\).  
  
 È possibile utilizzare la finestra di dialogo **Azioni personalizzate** per specificare un *modulo di destinazione*.  Un modulo di destinazione rappresenta il modulo visualizzato quando l'utente esegue l'azione personalizzata.  
  
 È anche possibile utilizzare la finestra di dialogo **Azioni personalizzate** per specificare la modalità in cui si desidera visualizzare le informazioni dell'elemento originale nel modulo di destinazione.  
  
 Nella tabella riportata di seguito vengono descritte le proprietà disponibili nella finestra di dialogo **Azioni personalizzate**.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**AddressLike**|Specifica come verrà indirizzato il modulo di destinazione.|  
|**Body**|Specifica come il corpo dell'elemento originale viene accodato al modulo di destinazione.|  
|**Enabled**|Indica se l'azione personalizzata è attivata.  Se questa proprietà è impostata su **false**, l'azione personalizzata è disabilitata.|  
|**Metodo**|Specifica il tipo di risposta disponibile quando viene eseguita l'azione personalizzata.  L'azione personalizzata può inviare o aprire il modulo oppure chiedere all'utente se desidera inviarlo o aprirlo.|  
|**Nome**|Specifica il nome interno che è possibile utilizzare per fare riferimento a questa azione personalizzata nel codice.|  
|**ShowOnRibbon**|Indica se visualizzare l'azione personalizzata sulla barra multifunzione dell'elemento originale.|  
|**SubjectPrefix**|Specifica il testo inserito all'inizio dell'oggetto del modulo di destinazione.|  
|**TargetForm**|Specifica il nome di classe messaggio del modulo di destinazione.  Ad esempio, digitare **IPM.Task** per aprire un modulo di attività.|  
|**Titolo**|Specifica l'etichetta del pulsante di azione personalizzato.|  
  
## Personalizzazione di un'azione personalizzata in fase di esecuzione  
 È anche possibile aggiungere un comportamento all'azione personalizzata utilizzando il codice.  Ad esempio, è possibile aggiungere codice che accetta i nomi dei destinatari di posta elettronica e li aggiunge come partecipanti a un nuovo elemento appuntamento.  Per eseguire questa operazione, gestire l'evento [CustomAction](HV05247448) dell'oggetto [Action](HV05247650).  
  
## Vedere anche  
 [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Associazione di un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  