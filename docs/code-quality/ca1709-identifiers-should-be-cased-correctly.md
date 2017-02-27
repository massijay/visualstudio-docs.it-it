---
title: "CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldBeCasedCorrectly"
  - "CA1709"
helpviewer_keywords: 
  - "CA1709"
  - "IdentifiersShouldBeCasedCorrectly"
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 29
---
# CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Categoria|Microsoft.Naming|  
|Breaking Change|Sostanziale \- se generato su assembly, spazi dei nomi, tipi, membri e parametri.<br /><br /> Non sostanziale – se generato su parametri di tipo generici.|  
  
## Causa  
 Il nome di un identificatore non è digitato correttamente relativamente all'uso di maiuscole e minuscole.  
  
 \-oppure\-  
  
 Il nome di un identificatore contiene un acronimo di due lettere e la seconda lettera è minuscola.  
  
 \-oppure\-  
  
 Il nome di un identificatore contiene un acronimo di tre o più lettere maiuscole.  
  
## Descrizione della regola  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
 Per convenzione i nomi di parametro sono basati sulla convenzione Camel, mentre i nomi di spazio dei nomi, di tipo e di membro utilizzano la convenzione Pascal.  In un nome conforme alla convenzione Camel, la prima lettera è minuscola, mentre la prima lettera di tutte le rimanenti parole del nome è maiuscola.  Esempi di nomi conformi alla convenzione Camel sono "packetSniffer", "ioFile" e "fatalErrorCode".  In un nome conforme alla convenzione Pascal, la prima lettera è maiuscola così come la prima lettera di tutte le rimanenti parole del nome.  Esempi di nomi conformi alla convenzione Pascal sono "PacketSniffer", "IOFile" e "FatalErrorCode".  
  
 Questa regola divide il nome in parole in base alle maiuscole e minuscole e confronta ogni parola di due lettere con un elenco di parole comuni inglesi composte da due lettere come "In" o "My".  Se non viene rilevata una corrispondenza, viene presupposto che la parola sia un acronimo.  La regola presuppone che si tratti di un acronimo quando rileva un nome contenente quattro lettere maiuscole di seguito o, alla fine del nome, tre lettere maiuscole di seguito.  
  
 Per convezione, gli acronimi di due lettere utilizzano solo lettere maiuscole, mentre gli acronimi di tre o più caratteri utilizzano la convenzione Pascal.  Gli esempi riportati di seguito utilizzano questa convenzione di denominazione: "DB", "CR", "Cpa" ed "Ecma".  I seguenti esempi violano la convenzione: "Io", "XML", "DoD" e, per i nomi non di parametri, "xp" e "cpl".  
  
 "ID" è scritto in maiuscole per causare una violazione di questa regola. 'Id' non è un acronimo bensì un'abbreviazione di 'identification'.  
  
## Come correggere le violazioni  
 Modificare il modo in modo che presenti le lettere maiuscole e minuscole corrette.  
  
## Esclusione di avvisi  
 È consigliabile escludere questo avviso se si dispone di convenzioni di denominazione proprie o se l'identificatore rappresenta un nome proprio, ad esempio il nome di una società o di una tecnologia.  
  
 È inoltre possibile aggiungere termini specifici, abbreviazioni e acronimi a un dizionario personalizzato di analisi codice.  I termini specificati nel dizionario personalizzato non provocheranno violazioni di questa regola.  Per ulteriori informazioni, vedere [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## Regole correlate  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)