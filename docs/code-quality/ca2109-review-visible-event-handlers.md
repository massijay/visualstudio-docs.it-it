---
title: "CA2109: Controllare i gestori di eventi visibili | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
helpviewer_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2109: Controllare i gestori di eventi visibili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 È stato rilevato un metodo di gestione eventi pubblico o protetto.  
  
## Descrizione della regola  
 Un metodo di gestione eventi visibile esternamente presenta un problema di sicurezza che richiede revisione.  
  
 I metodi di gestione eventi non devono essere esposti se non assolutamente necessario.  Un gestore eventi, un tipo delegato, che richiama il metodo esposto può essere aggiunto a qualsiasi evento purché le firme di gestore ed evento corrispondano.  Gli eventi possono potenzialmente essere generati da qualsiasi codice e in molti casi vengono generati da codice di sistema altamente attendibile in risposta ad azioni dell'utente come la scelta di un pulsante.  L'aggiunta di un controllo di sicurezza a un metodo di gestione eventi non impedisce al codice di registrare un gestore eventi che richiama il metodo.  
  
 Una richiesta non può proteggere in modo affidabile un metodo richiamato da un gestore eventi.  Le richieste di sicurezza consentono di proteggere il codice da chiamanti non attendibili esaminando i chiamanti nello stack di chiamate.  Il codice che aggiunge un gestore eventi a un evento non è necessariamente presente nello stack di chiamate quando vengono eseguiti i metodi del gestore eventi.  Pertanto, lo stack di chiamate può contenere solo chiamanti altamente attendibili quando viene richiamato il metodo del gestore eventi,  causando la riuscita delle richieste eseguite dal metodo del gestore eventi.  Inoltre, le autorizzazioni richieste potrebbero essere asserite quando il metodo viene richiamato.  Pertanto, il rischio di non correggere una violazione di questa regola può essere valutato solo dopo aver rivisto il metodo di gestione eventi.  Quando si rivede il codice, considerare quanto segue:  
  
-   Valutare se il gestore eventi esegue operazioni pericolose, ad esempio l'asserzione di autorizzazioni o l'eliminazione di autorizzazioni di codice non gestito.  
  
-   Valutare quali sono le minacce alla sicurezza poste dal codice, dal momento che può essere eseguito in qualsiasi momento solo con chiamanti altamente attendibili nello stack.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rivedere il metodo e valutare quanto segue:  
  
-   Valutare se è possibile rendere non pubblico il metodo di gestione eventi.  
  
-   Valutare se è possibile spostare tutte le funzionalità pericolose al di fuori del gestore eventi.  
  
-   In caso si imponga una richiesta di sicurezza, valutare se possa essere eseguita in un altro modo.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola solo dopo un'attenta revisione della sicurezza per assicurarsi che il codice non comporti una minaccia alla sicurezza.  
  
## Esempio  
 Nel codice riportato di seguito viene illustrato un metodo di gestione eventi che può essere utilizzato in modo improprio da codice dannoso.  
  
 [!code-cs[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## Vedere anche  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 [Security Demands](http://msdn.microsoft.com/it-it/324c14f8-54ff-494d-9fd1-bfd20962c8ba)