---
title: "ActivityDesigner InvokeMethod | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.InvokeMethod.UI"
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner InvokeMethod
L'ActivityDesigner **InvokeMethod** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.InvokeMethod>.  
  
## Attività InvokeMethod  
 L'attività <xref:System.Activities.Statements.InvokeMethod> chiama un metodo pubblico di un oggetto o tipo specificato.  
  
### Utilizzo dell'ActivityDesigner InvokeMethod  
 L'ActivityDesigner **InvokeMethod** è disponibile nella categoria **Primitive** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti** di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **InvokeMethod** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.InvokeMethod> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito InvokeMethod.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **InvokeMethod** o nella casella **DisplayName** della griglia delle proprietà.  
  
### Proprietà di InvokeMethod  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeMethod> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeMethod>.Il valore predefinito è InvokeMethod.<br /><br /> Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Nome del metodo da richiamare quando viene eseguita l'attività.Il metodo chiamato deve essere dichiarato come **public**.È possibile modificare questa proprietà nell'area della finestra di progettazione.Si tratta di una proprietà obbligatoria.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Raccolta di parametri del metodo chiamato.I parametri devono essere aggiunti alla raccolta nello stesso ordine in cui vengono visualizzati nella firma del metodo.Nella griglia delle proprietà fare clic sul pulsante con i puntini di sospensione nel campo **Parametri** per visualizzare la finestra di dialogo **Parametri** che consente di impostare tale proprietà.Fare clic sul pulsante **Crea argomento** per aggiungere i parametri.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Valore restituito dalla chiamata del metodo.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Specifica se il metodo viene chiamato in modo asincrono.Il valore predefinito è **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Oggetto contenente il metodo da chiamare.È possibile modificare questa proprietà nell'area della finestra di progettazione.<br /><br /> È necessario impostare <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Tipo dell'oggetto <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.È possibile modificare questa proprietà nell'area della finestra di progettazione.È necessario impostare questa proprietà solo se il metodo chiamato è statico.|  
  
 Per passare parametri come parametro C\# **out**, ad esempio `Method1(out myParam)),`, è consigliabile utilizzare **OutArgument** anziché **InOutArgument**  
  
 Non è possibile richiamare metodi con gli argomenti chiamati **TargetObject** o **Result** utilizzando l'attività <xref:System.Activities.Statements.InvokeMethod>.Il motivo di ciò è che l'attività <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> e <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
 L'algoritmo per la registrazione dei parametri in <xref:System.Activities.Activity.CacheMetadata%2A> viene mostrato nell'elenco seguente:  
  
1.  Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.  
  
2.  Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.  
  
3.  Scorrere la raccolta <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> e registrare ogni argomento.  
  
 L'eccezione risultante è di tipo <xref:System.Activities.InvalidWorkflowException> e presenta il messaggio seguente: 'InvokeMethod': Esiste già una variabile, RuntimeArgument o DelegateArgument con il nome 'TargetObject'.I nomi devono essere univoci in un ambito di ambiente.  
  
 Questa restrizione non si applica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> e <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> perché non sono argomenti del flusso di lavoro e pertanto non sono registrati nella raccolta <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> dell'attività <xref:System.Activities.Statements.InvokeMethod> nel metodo <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
## Vedere anche  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)