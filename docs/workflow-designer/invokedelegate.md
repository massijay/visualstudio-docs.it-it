---
title: "InvokeDelegate | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InvokeDelegate Designer"
  - "System.Activities.Statements.InvokeDelegate.UI"
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "sdanie"
manager: "erikre"
---
# InvokeDelegate
La finestra di progettazione **InvokeDelegate** viene utilizzata per creare e configurare un'attività <xref:System.Activities.Statements.InvokeDelegate>.  
  
## L'attività InvokeDelegate  
 L'oggetto <xref:System.Activities.Statements.InvokeDelegate> chiama un delegato pubblico.  
  
### Utilizzo dell'ActivityDesigner InvokeDelegate  
 L'ActivityDesigner **InvokeDelegate** è disponibile nella categoria **Primitive** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti** di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **InvokeDelegate** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.InvokeDelegate> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito InvokeDelegate.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **InvokeDelegate** o nella casella **DisplayName** della griglia delle proprietà.  
  
### Proprietà di InvokeDelegate  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.InvokeDelegate> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeDelegate>.Il valore predefinito è InvokeDelegate.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nome del metodo <xref:System.Activities.Statements.ActivityDelegate> da richiamare quando viene eseguita l'attività.È possibile modificare questa proprietà nell'area della finestra di progettazione.Si tratta di una proprietà obbligatoria.|  
|<xref:System.Activities.Statements.InvokeMethod.DelegateArguments%2A>|False|Raccolta dell'argomento del delegato chiamato.Le chiavi sono i nomi degli oggetti <xref:System.Activities.Statements.ActivityDelegateParameter> su <xref:System.Activities.Statements.ActivityDelegate> e i valori sono gli argomenti le cui espressioni vengono valutate ed assegnate agli oggetti corrispondenti <xref:System.Activities.Statements.ActivityDelegateParameter>.Nella griglia delle proprietà fare clic sul pulsante con i puntini di sospensione nel campo **DelegateArguments** per visualizzare la finestra di dialogo **DelegateArguments** che consente di impostare tale proprietà.Fare clic sul campo **Crea argomento** per aggiungere gli argomenti.|  
  
## Vedere anche  
 [Procedura: definire e utilizzare delegati di attività in Progettazione del flusso di lavoro](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)