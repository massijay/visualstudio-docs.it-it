---
title: "ActivityDesigner WriteLine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.WriteLine.UI"
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ActivityDesigner WriteLine
L'ActivityDesigner **WriteLine** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.WriteLine>.  
  
## Attività WriteLine  
 L'attività <xref:System.Activities.Statements.Writeline> scrive il testo in un oggetto <xref:System.IO.TextWriter> specificato.Se non è specificato alcun oggetto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.Writeline> scrive il testo sulla console.  
  
### Utilizzo dell'ActivityDesigner WriteLine  
 L'ActivityDesigner **WriteLine** è disponibile nella categoria **Primitive** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti** di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **WriteLine** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.WriteLine> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito WriteLine.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **WriteLine** o nella casella **DisplayName** della griglia delle proprietà.  
  
### Proprietà di WriteLine  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.WriteLine> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.WriteLine>.Il valore predefinito è WriteLine.Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Testo da scrivere.Per impostare la proprietà, digitare un'espressione Visual Basic nella casella **Text** sull'ActivityDesigner **WriteLine** o nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|Oggetto <xref:System.IO.TextWriter> nel quale <xref:System.Activities.Statements.WriteLine> scrive <xref:System.Activities.Statements.WriteLine.Text%2A>.Il valore predefinito corrisponde alla console.|  
  
## Vedere anche  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)