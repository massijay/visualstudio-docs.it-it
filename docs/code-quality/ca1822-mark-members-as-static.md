---
title: "CA1822: Contrassegna i membri come statici | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkMembersAsStatic"
  - "CA1822"
helpviewer_keywords: 
  - "MarkMethodsAsStatic"
  - "CA1822"
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1822: Contrassegna i membri come statici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|CheckId|CA1822|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale \- Se il membro non è visibile all'esterno dell'assembly, indipendentemente dalla modifica apportata.  Non sostanziale \- Se si imposta semplicemente il membro su un membro di istanza con la parola chiave `this`.<br /><br /> Sostanziale \- Se il membro viene configurato da membro di istanza a membro statico ed è visibile all'esterno dell'assembly.|  
  
## Causa  
 Un membro che non accede ai dati sull'istanza non è contrassegnato come statico \(Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Descrizione della regola  
 I membri che non accedono ai dati di istanza o non chiamano metodi di istanza possono essere contrassegnati come static \(Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  Tramite il compilatore verranno quindi inviati siti di chiamata non virtuali a tali membri.  L'emissione di siti di chiamata non virtuali impedirà un controllo in fase di runtime per ogni chiamata che accerti che il puntatore dell'oggetto corrente sia diverso da null.  Si potrà così ottenere un sensibile miglioramento delle prestazioni per codici sensibili alle prestazioni.  In alcuni casi, l'accesso non riuscito all'istanza dell'oggetto corrente rappresenta un problema di correzione.  
  
## Come correggere le violazioni  
 Contrassegnare il membro come statico \(o Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) o utilizzare 'this'\/'Me' nel corpo del metodo, se appropriato.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura per il codice fornito in precedenza per il quale la correzione rappresenterebbe una modifica sostanziale.  
  
## Regole correlate  
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)