---
title: "Avvisi di denominazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.namingrules"
helpviewer_keywords: 
  - "avvisi dell'analisi codice gestito, denominazione"
  - "avvisi di denominazione"
  - "avvisi, denominazione"
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Avvisi di denominazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di denominazione supportano la conformità alle convenzioni di denominazione delle linee guida di progettazione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## In questa sezione  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Questa regola presuppone che un membro di enumerazione con un nome che contiene la parola "reserved" non sia attualmente utilizzato, ma sia un segnaposto che dovrà essere rinominato o rimosso in una versione futura.  La ridenominazione o rimozione di un membro è ritenuta una modifica sostanziale.|  
|[CA1713: Non utilizzare il prefisso Before o After negli eventi](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Il nome di un evento inizia con "Before" o "After".  Per denominare eventi correlati generati in una sequenza specifica, utilizzare i tempi verbali presente o passato per indicare la posizione relativa nella sequenza di azioni.|  
|[CA1714: Le enumerazioni con Flags devono avere nomi plurali](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Un'enumerazione pubblica dispone dell'attributo System.FlagsAttribute e il nome non termina per "s".  Ai tipi contrassegnati con FlagsAttribute sono assegnati nomi plurali perché tale attributo indica che è possibile specificare più valori.|  
|[CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Il nome di un identificatore visibile esternamente contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.|  
|[CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Gli identificatori per spazi dei nomi, tipi, membri e parametri non possono differire solo in base a maiuscole e minuscole poiché ai linguaggi destinati a Common Language Runtime non è richiesta la distinzione tra maiuscole e minuscole.|  
|[CA1715: Gli identificatori devono contenere il prefisso corretto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Il nome di un'interfaccia visibile esternamente non inizia con una "I" maiuscola.  Il nome di un parametro di tipo generico su un tipo o metodo visibile esternamente non inizia con una "T" maiuscola.|  
|[CA1720: Gli identificatori non devono contenere nomi di tipo](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Il nome di un parametro in un membro visibile esternamente contiene un nome di tipo di dati oppure il nome di un membro visibile esternamente contiene un nome di tipo di dati specifico del linguaggio.|  
|[CA1722: Gli identificatori non devono contenere il prefisso non corretto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Per convenzione, solo determinati elementi di programmazione presentano nomi che iniziano con un prefisso specifico.|  
|[CA1711: Gli identificatori non devono contenere un suffisso non corretto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Per convenzione, solo i nomi dei tipi che estendono determinati tipi di base o che implementano determinate interfacce o dei tipi derivati da questi tipi devono terminare con suffissi specifici riservati.  Gli altri nomi di tipi non devono utilizzare questi suffissi riservati.|  
|[CA1717: Solo le enumerazioni con FlagsAttribute devono avere nomi plurali](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|In base alle convenzioni di denominazione, un nome plurale in un'enumerazione indica che è possibile specificare più valori di enumerazione contemporaneamente.|  
|[CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Una denominazione coerente dei parametri in una gerarchia di override aumenta la funzionalità degli override di metodo.  Un nome di parametro in un metodo derivato diverso dal nome nella dichiarazione di base può provocare confusione sulla natura del metodo, ovvero se si tratta di un override del metodo di base o di un nuovo overload del metodo.|  
|[CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Un nome di parametro deve comunicare il significato di un parametro e un nome di membro deve comunicare il significato di un membro.  Le progettazioni in cui questi nomi coincidono sono rare.  Assegnare a un parametro lo stesso nome del relativo membro non è intuitiva e rende più complesso l'utilizzo della libreria.|  
|[CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Ogni parola nella stringa di risorsa è suddivisa in token basati sulla distinzione tra maiuscole e minuscole.  Ogni combinazione di due token contigui viene controllata in base alla libreria del correttore ortografico Microsoft.  Se riconosciuta, la parola produce una violazione della regola.|  
|[CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Una stringa di risorsa contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.|  
|[CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|I nomi dei tipi non devono corrispondere ai nomi degli spazi dei nomi definiti nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  La violazione di questa regola può ridurre l'utilizzabilità della libreria.|  
|[CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Per convenzione i nomi degli identificatori non contengono il carattere di sottolineatura \(\_\).  In base a questa regola vengono controllati spazi dei nomi, tipi, membri e parametri.|  
|[CA1721: I nomi delle proprietà non devono corrispondere ai metodi get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Il nome di un membro pubblico o protetto inizia con "Get" e corrisponde in altro modo al nome di una proprietà pubblica o protetta. Le proprietà e i metodi "Get" devono avere nomi che distinguano chiaramente la loro funzione.|  
|[CA1716: Gli identificatori non devono corrispondere a parole chiave](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Un nome di spazio dei nomi o di tipo corrisponde a una parola chiave riservata in un linguaggio di programmazione.  Gli identificatori di spazi dei nomi e tipi non devono corrispondere a parole chiave definite dai linguaggi con destinazione Common Language Runtime.|  
|[CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)|Il nome di un identificatore visibile esternamente include un termine per il quale esiste un termine alternativo preferito.  In alternativa, il nome include il termine "Flag" o "Flags".|  
|[CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Per convenzione i nomi di parametro sono basati sulla convenzione Camel, mentre i nomi di spazio dei nomi, tipo e membro utilizzano la convenzione Pascal.|  
|[CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Il nome di un identificatore contiene più parole, fra cui almeno una che sembra essere composta e digitata in modo non corretto con distinzione tra maiuscole e minuscole.|  
|[CA1712: Non utilizzare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|I nomi dei membri di enumerazione non hanno come prefisso il nome del tipo poiché si prevede che le informazioni sul tipo vengano fornite dagli strumenti di sviluppo.|  
|[CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Per convenzione i nomi dei tipi che estendono determinati tipi di base o che implementano determinate interfacce o dei tipi derivati da questi tipi contengono un suffisso associato al tipo di base o all'interfaccia.|