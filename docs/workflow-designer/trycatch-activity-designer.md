---
title: "ActivityDesigner TryCatch | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TryCatch.UI"
  - "System.Activities.Statements.Catch`1.UI"
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner TryCatch
L'ActivityDesigner **TryCatch** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.TryCatch>.  
  
## Attività TryCatch  
 L'attività <xref:System.Activities.Statements.TryCatch> contiene un'attività <xref:System.Activities.Statements.TryCatch.Try%2A>, una raccolta di **Catch\<TException\>** e un'attività <xref:System.Activities.Statements.TryCatch.Finally%2A>.Un oggetto <xref:System.Activities.Statements.Catch%601> di tipo **TException** contiene una proprietà <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> e una proprietà <xref:System.Activities.Statements.Catch%601.Action%2A>,che vengono utilizzate insieme per implementare un meccanismo tipico di gestione degli errori basato sulle eccezioni.Un'attività <xref:System.Activities.Statements.TryCatch> tenta di eseguire la relativa attività <xref:System.Activities.Statements.TryCatch.Try%2A>.Se l'attività <xref:System.Activities.Statements.TryCatch.Try%2A> genera un'eccezione, l'attività <xref:System.Activities.Statements.TryCatch> utilizza la relativa raccolta **Catch\<TException\>** in modo da creare una corrispondenza con l'eccezione.Se esiste una corrispondenza, viene eseguita la proprietà <xref:System.Activities.Statements.Catch%601.Action%2A> dell'oggetto **Catch\<TException\>** corrispondente, che funge da logica di gestione degli errori per l'eccezione.Se le attività nella sezione di <xref:System.Activities.Statements.TryCatch.Try%2A> o le attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> terminano in modo corretto, l'attività di <xref:System.Activities.Statements.TryCatch> esegue la relativa attività di <xref:System.Activities.Statements.TryCatch.Finally%2A>.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Eccezioni](../Topic/Exceptions.md).  
  
### Utilizzo dell'ActivityDesigner TryCatch  
 L'ActivityDesigner **TryCatch** è disponibile nella categoria **Gestione errori** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** a sinistra di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **TryCatch** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.TryCatch> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito TryCatch.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **TryCatch** o nella casella **DisplayName** della griglia delle proprietà.Le altre proprietà devono essere modificate nell'area dell'ActivityDesigner **TryCatch**.  
  
 Fare clic sul pulsante di espansione nell'angolo superiore destro dell'ActivityDesigner **TryCatch** per visualizzare le caselle **Try**, **Catches** e **Finally** in modalità espansa.Per aggiungere un catch, fare clic sul pulsante **Aggiungi nuovo catch** nell'ActivityDesigner **TryCatch**.Il pulsante diventa una casella combinata del tipo.Selezionare un tipo di eccezione e premere INVIO per aggiungere il catch.Dopo aver aggiunto un elemento **Catch**, l'area dei catch si espande. È quindi possibile rilasciare un'attività nel catch in modo da definirne la logica di esecuzione.Si noti la presenza di una casella di testo a destra dell'area dei catch espansa.Questa casella consente di assegnare un nome alla variabile dell'eccezione.La variabile dell'eccezione può essere utilizzata solo per le attività all'interno dello stesso oggetto **Catch**.  
  
 L'ActivityDesigner **TryCatch** non supporta la modifica di **Catch**.Se si desidera modificare il tipo di eccezione, è necessario eliminare l'oggetto **Catch** ed aggiungere un nuovo.Un oggetto **Catch** può essere eliminato selezionandolo ed eliminandolo o utilizzando il menu **Elimina** nel menu di scelta rapida cui è possibile accedere facendo clic con il pulsante destro del mouse.  
  
### Proprietà di TryCatch  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TryCatch> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Consente di specificare il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TryCatch>.Il percorso predefinito è TryCatch.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|L'attività è stata eseguita per prima quando viene eseguito <xref:System.Activities.Statements.TryCatch>.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Raccolta di elementi **Catch** da verificare quando l'attività <xref:System.Activities.Statements.TryCatch.Try%2A> genera un'eccezione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|L'attività da eseguire quando <xref:System.Activities.Statements.TryCatch.Try%2A> e qualsiasi attività necessaria nella raccolta <xref:System.Activities.Statements.TryCatch.Catches%2A> completano l'esecuzione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
  
## Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)