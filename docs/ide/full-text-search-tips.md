---
title: "Suggerimenti per la ricerca full-text | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hv_search"
helpviewer_keywords: 
  - "Help Viewer 2.0, suggerimenti per la ricerca full-text"
  - "suggerimenti per la ricerca full-text [Help Viewer 2.0]"
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Suggerimenti per la ricerca full-text
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Uno dei metodi più utili per individuare le informazioni della guida è quello di eseguire una ricerca full\-text.  Per perfezionare e personalizzare i risultati, è necessario comprendere il modo in cui la sintassi influisce sulla query.  In questo argomento vengono forniti suggerimenti, procedure e informazioni dettagliate sulla sintassi per elaborare meglio le query.  
  
## Suggerimenti per la ricerca full\-text  
 È possibile creare ricerche più mirate che restituiscono solo gli argomenti che interessano se si comprende come la Guida interpreta la formattazione utilizzata nelle query.  Questi formati includono caratteri speciali, parole riservate e filtri.  
  
### Indicazioni generali  
 Nella tabella seguente sono incluse alcune regole e linee guida di base per lo sviluppo di query di ricerca nella Guida.  
  
|Sintassi|Descrizione|  
|--------------|-----------------|  
|Distinzione fra maiuscole e minuscole|Nelle ricerche non viene applicata la distinzione tra maiuscole e minuscole.  Sviluppare i criteri di ricerca utilizzando i caratteri maiuscoli o minuscoli.  Ad esempio, le parole "OLE" e "ole" restituiscono gli stessi risultati.|  
|Combinazioni di caratteri|Non è possibile cercare solo le singole lettere \(a\-z\) o i numeri \(da 0 a 9\).  Se si tenta di individuare determinate parole riservate, ad esempio "e", "da" e "con", queste verranno ignorate.  Per ulteriori informazioni, vedere "Parole ignorate nelle ricerche \(parole non significative\)" più avanti in questo argomento.|  
|Ordine di valutazione|Le query di ricerca vengono valutate da sinistra a destra.|  
  
### Sintassi di ricerca  
 Se si specifica una stringa di ricerca che include più parole, ad esempio "parola1 parola2", tale stringa è equivalente a digitare "parola1 E parola2", che restituisce solo gli argomenti contenenti tutte le singole parole nella stringa di ricerca.  
  
> [!IMPORTANT]
>  1.  Le ricerche di frasi non sono supportate.  Se si specificano più parole in una stringa di ricerca, gli argomenti restituiti comprenderanno tutte le parole specificate ma non necessariamente la frase esatta specificata.  
> 2.  Utilizzare gli operatori logici per specificare la relazione tra le parole nella frase di ricerca.  È possibile includere gli operatori logici, come AND, OR, NOT e NEAR per limitare ulteriormente la ricerca.  Ad esempio, se si cerca "dichiarazione NEAR unione", i risultati della ricerca includeranno gli argomenti contenenti le parole "dichiarazione" e "unione" separate da poche parole.  Per ulteriori informazioni, vedere [Operatori logici nelle espressioni di ricerca](../ide/logical-operators-in-search-expressions.md).  
  
### Filtri  
 È possibile limitare ulteriormente i risultati della ricerca utilizzando gli operatori di ricerca avanzati.  La Guida comprende tre categorie che è possibile utilizzare per filtrare i risultati di una ricerca full\-text: titolo, codice e parola chiave.  Per ulteriori informazioni, vedere [Operatori di ricerca avanzati nelle espressioni di ricerca](../ide/advanced-search-operators-in-search-expressions.md).  
  
### Classificazione dei risultati di ricerca  
 L'algoritmo di ricerca applica determinati criteri per classificare i risultati della ricerca nella parte più alta o più bassa dell'elenco risultati.  In generale:  
  
1.  Il contenuto che include le parole della ricerca nel titolo viene classificato in una posizione più alta rispetto a un contenuto che non ha le parole della ricerca nel titolo.  
  
2.  Il contenuto che include le parole della ricerca in prossimità viene classificato in una posizione più alta rispetto a un contenuto che non ha le parole di ricerca in prossimità.  
  
3.  Il contenuto che contiene una maggiore densità di parole di ricerca viene classificato in una posizione più alta rispetto a un contenuto con una densità inferiore di parole di ricerca.  
  
### Parole ignorate nelle ricerche \(parole non significative\)  
 Le parole o i numeri di uso frequente, che sono talvolta denominati parole non significative, vengono automaticamente ignorati durante una ricerca full\-text.  Ad esempio, se si cerca la frase "codice gestito", i risultati della ricerca includeranno gli argomenti contenenti la parola "codice" ma non la parola "gestito".  
  
## Vedere anche  
 [Individuare informazioni](../ide/locate-information.md)   
 [Operatori logici nelle espressioni di ricerca](../ide/logical-operators-in-search-expressions.md)