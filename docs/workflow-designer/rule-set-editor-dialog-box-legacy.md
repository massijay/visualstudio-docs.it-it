---
title: "Finestra di dialogo Editor set di regole (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleSetDialog.UI"
helpviewer_keywords: 
  - "Finestra di dialogo Editor set di regole"
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Finestra di dialogo Editor set di regole (legacy)
In questo argomento viene descritto come utilizzare la finestra di dialogo **Editor set di regole** in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy.Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 La finestra di dialogo **Editor set di regole** viene utilizzata per creare e modificare i set di regole [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), serializzati a un file con estensione .rules.  
  
> [!NOTE]
>  Se si desidera aprire il file con estensione rules con **Editor XML con codifica**, chiudere prima la finestra di progettazione associata per il flusso di lavoro o attività.  
  
 Per informazioni sull'accesso alla finestra di dialogo **Editor set di regole**, vedere [Procedura: creare un set di regole per l'attività PolicyActivity \(legacy\)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  L'editor delle regole della [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy che viene utilizzato per fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] non supporta il multitargeting.  
  
 Nella tabella seguente sono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Editor set di regole**.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|--------------------------------------|-----------------|  
|**Aggiungi regola**|Aggiunge una nuova definizione della regola nuova nell’insieme di regole.|  
|**Elimina**|Elimina la regola selezionata dall’insieme di regole.|  
|**Concatenamento**|Specifica quale tipo di concatenamento diretto utilizzare con l’insieme di regole.Sono disponibili le seguenti opzioni:<br /><br /> -   **Concatenamento completo** che specifica di utilizzare tutti i meccanismi di concatenamento diretto: implicito, con attribuzione del metodo ed esplicito utilizzando una funzione **Update**.<br />-   **Sequenziale** che specifica di non utilizzare alcun concatenamento diretto.<br />-   **Solo aggiornamento esplicito** che specifica di eseguire soltanto concatenamento diretto sulle azioni di **Aggiornamento**.<br /><br /> Per ulteriori informazioni sul concatenamento diretto, vedere [Utilizzo di attività olicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Nome**|Intestazione di colonna dell’elenco dell’insieme di regole.Fare clic per ordinare l'elenco di regole per nome.|  
|**Priority**|Intestazione di colonna dell’elenco dell’insieme di regole.Fare clic per ordinare l'elenco di regole per priorità.|  
|**Rivalutazione**|Intestazione di colonna dell’elenco dell’insieme di regole.Fare clic per ordinare l'elenco di regole per tipo di rivalutazione.|  
|**Anteprima della regola**|Intestazione di colonna dell’elenco dell’insieme di regole.Fare clic per ordinare l'elenco di regole per anteprima di una condizione della regola e delle azioni.|  
|**Nome:**|Immettere il nome della regola.|  
|**Priorità:**|Immettere una priorità per la regola.La priorità predefinita è 0.|  
|**Rivalutazione:**|Specifica quale tipo di rivalutazione della regola utilizzare con la regola.Sono disponibili le seguenti opzioni:<br /><br /> -   **Sempre** che fa in modo che la regola sia rivalutata in base alle esigenze.<br />-   **Mai**, che fa in modo che la regola non sia mai rivalutata.In questo caso una regola viene eseguita solo una volta.|  
|**Attiva**|Selezionare per rendere attiva la regola.|  
|**Condizione:**|Immettere un'espressione per la condizione della regola.Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|  
|**Azioni THEN:**|Immettere l'espressione per azioni THEN.Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|  
|**Azioni ELSE:**|Immettere l'espressione per azioni ELSE.Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|  
|**OK**|Fare clic per salvare l’insieme di regole in un file con estensione rules.|  
  
 Per ulteriori informazioni sugli insiemi di regole, vedere [Utilizzo di attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## Immissione di espressioni di condizioni e azioni  
 Immettere espressioni per la Condizione e le azioni THEN ed ELSE come testo nelle rispettive caselle di testo nella finestra di dialogo **Editor dell’insieme di regole**.È possibile digitare **this.** nell'editor per fare riferimento a campi, proprietà e metodi utilizzati nel flusso di lavoro, tramite un menu di tipo IntelliSense.In alternativa, è possibile digitare direttamente il nome di un membro del flusso di lavoro.È possibile richiamare metodi statici sui tipi a cui viene fatto riferimento digitando il nome della classe seguito dal nome del metodo.  
  
 È possibile aggiungere operatori logici alla condizione, ad esempio E, O e NON.È anche possibile aggiungere predicati.Un predicato è composto da un operatore binario e due operandi.Gli operatori binari supportati sono \=\=, \>, \<, \>\=, e \<\=.Gli operandi supportati sono membri pubblici ai quali è stato assegnato un valore costante, una funzione aritmetica e un ambito.  
  
 È possibile specificare il tipo per il confronto ed è possibile confrontare a **null** o a una stringa vuota.È possibile annidare chiamate ai membri su una variabile contenente un tipo complesso, ad esempio, `this.Address.State == "WA"`.  
  
 Le espressioni supportano gli operatori seguenti:  
  
-   operatori relazionali: \=\=, \=, \!\=  
  
-   Operatori di confronto: \<, \<\=, \>, \>\=  
  
-   Operatori aritmetici: \+, \- , \*, \/, MOD  
  
-   Operatori logici: AND, &&, OR, &#124;&#124;, NOT, \!  
  
-   Operatori bit per bit: &, &#124;  
  
 La precedenza di operatori dell’espressione segue le regole di precedenza dell’operatore C\#.  
  
 Per ulteriori informazioni sulle condizioni, vedere [Using Conditions in Workflows](http://msdn.microsoft.com/it-it/541211f5-d382-4810-894f-71f00b34fa77).  
  
### Funzioni Halt e Aggiorna  
 Le espressioni **Azioni THEN:** e **azioni ELSE:** supportano le funzioni **Halt** e **Update**.Per utilizzare la funzione **Halt**, digitare **Halt** in una casella di testo **Azione THEN:** o **Azione ELSE:**.L’azione **Halt** causa l’immediata interruzione dell’esecuzione dell’insieme di regole e restituisce il controllo al codice di chiamata.Con il concatenamento diretto si utilizza la funzione **Update**.  
  
 L’istruzione **Update** può essere espressa nell'editor in uno dei due moduli; entrambi i moduli sono mostrati nell'esempio seguente:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Per ulteriori informazioni sull’utilizzo di **Update** con concatenamento diretto, vedere [Utilizzo di PolicyActivity Activity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## Vedere anche  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Finestra di dialogo Seleziona set di regole \(legacy\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Utilizzo di condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)