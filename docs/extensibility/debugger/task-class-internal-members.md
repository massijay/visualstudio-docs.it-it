---
title: Classe - membri interni Task | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 21acb0a52dfde7ad565e9764e2a333a9925a2171
ms.lasthandoff: 02/22/2017

---
# <a name="task-class---internal-members"></a>Classe attività - membri interni
In questo argomento vengono descritti i membri interni della <xref:System.Threading.Tasks.Task?displayProperty=fullName>classe che consentono di implementare un debugger personalizzate.</xref:System.Threading.Tasks.Task?displayProperty=fullName> Per informazioni generali sulla classe, vedere il <xref:System.Threading.Tasks.Task>argomento di riferimento.</xref:System.Threading.Tasks.Task>  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questi membri interni di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Membri  
  
### <a name="methods"></a>Metodi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo SetNotificationForWaitCompletion](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Imposta o Cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[Metodo NotifyDebuggerOfWaitCompletion](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Metodo segnaposto utilizzato come destinazione del punto di interruzione dal debugger.|  
  
### <a name="fields"></a>Campi  
  
|Name|Descrizione|  
|----------|-----------------|  
|[m_action viene](../../extensibility/debugger/m-action-field.md)|Delegato che rappresenta il codice da eseguire nel <xref:System.Threading.Tasks.Task>oggetto.</xref:System.Threading.Tasks.Task>|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Memorizza le proprietà aggiuntive di <xref:System.Threading.Tasks.Task>oggetto.</xref:System.Threading.Tasks.Task>|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Il campo sottostante per la <xref:System.Threading.Tasks.Task?displayProperty=fullName>Proprietà parent.</xref:System.Threading.Tasks.Task?displayProperty=fullName>|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Archivia le informazioni sullo stato corrente di <xref:System.Threading.Tasks.Task>oggetto.</xref:System.Threading.Tasks.Task>|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Oggetto che rappresenta i dati che verranno utilizzati dall'azione.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Il campo sottostante per la <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>proprietà.</xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Il successivo identificatore disponibile per un <xref:System.Threading.Tasks.Task>oggetto.</xref:System.Threading.Tasks.Task>|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica che l'attività è stata annullata prima ha raggiunto lo stato di esecuzione o che l'attività ha confermato l'annullamento relativo e completata senza eccezioni.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica che l'attività è in esecuzione.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica che l'attività completata a causa di un'eccezione non gestita.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica che l'attività esecuzione completata correttamente.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica che l'attività ha terminato l'esecuzione del delegato e in modo implicito in attesa per il completamento delle attività figlio collegate.|  
  
## <a name="remarks"></a>Note  
 I seguenti metodi interni sono utili per un motore di debug perché contrassegnate l'ingresso alla <xref:System.Threading.Tasks.Task>esecuzione di codice:</xref:System.Threading.Tasks.Task>  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Elementi interni di estensione parallela per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
