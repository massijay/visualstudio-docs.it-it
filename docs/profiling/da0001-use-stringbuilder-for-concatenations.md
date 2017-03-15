---
title: "DA0001: Utilizzare StringBuilder per le concatenazioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0001"
  - "vs.performance.rules.DAUseStringBuilder"
  - "vs.performance.1"
  - "vs.performance.rules.DA0001"
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# DA0001: Utilizzare StringBuilder per le concatenazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0001|  
|Categoria|Utilizzo di .NET Framework|  
|Metodi di profilatura|Campionamento<br /><br /> Strumentazione|  
|Messaggio|Considerare l'utilizzo di StringBuilder per le concatenazioni di stringhe|  
|Tipo messaggio|Avviso|  
  
## Causa  
 Le chiamate a System.String.Concat sono una percentuale significativa dei dati di profilatura.  Considerare l'utilizzo della classe <xref:System.Text.StringBuilder> per costruire stringhe da più segmenti.  
  
## Descrizione della regola  
 Un oggetto <xref:System.String> non è modificabile.  Pertanto, qualsiasi modifica alla stringa crea un nuovo oggetto stringa e il Garbage Collection dell'originale.  Questo comportamento è lo stesso sia se si chiama in modo esplicito String.Concat sia se si utilizzano gli operatori di concatenazione di stringhe quali \+ o \+ \=..  Le prestazioni del programma possono calare se questi metodi vengono chiamati con frequenza, ad esempio quando vengono aggiunti caratteri a una stringa in un ciclo ridotto.  
  
 La classe StringBuilder è un oggetto modificabile e, a differenza di System.String, la maggior parte dei metodi di StringBuilder che modificano un'istanza di questa classe restituisce un riferimento a quella stessa istanza.  È possibile inserire caratteri o aggiungere testo in coda a un'istanza di StringBuilder e rimuovere o sostituire i caratteri nell'istanza senza dover allocare una nuova istanza ed eliminare l'istanza originale.  
  
## Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare a [Visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilo di campionamento.  Trovare le sezioni del programma che fanno maggior uso della concatenazione di stringhe.  Utilizzare la classe StringBuilder per le modifiche di stringa complesse, comprese le operazioni frequenti di concatenazione di stringhe.  
  
 Per ulteriori informazioni su come utilizzare le stringhe, [Operazioni sulle stringhe](http://go.microsoft.com/fwlink/?LinkId=177816) sezione del [Capitolo 5 relativo al miglioramento delle prestazioni del codice gestito](http://go.microsoft.com/fwlink/?LinkId=177817) nella libreria Microsoft Patterns and Practices.