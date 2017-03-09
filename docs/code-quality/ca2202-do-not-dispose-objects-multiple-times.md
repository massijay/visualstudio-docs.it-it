---
title: "CA2202: Non eliminare oggetti pi&#249; volte | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2202"
  - "Do not dispose objects multiple times"
  - "DoNotDisposeObjectsMultipleTimes"
helpviewer_keywords: 
  - "CA2202"
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2202: Non eliminare oggetti pi&#249; volte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un'implementazione di metodo contiene percorsi del codice che potrebbero causare più chiamate a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o a un equivalente di Dispose, ad esempio un metodo Close\(\) su alcuni tipi, sullo stesso oggetto.  
  
## Descrizione della regola  
 Un metodo <xref:System.IDisposable.Dispose%2A> implementato correttamente può essere chiamato più volte senza generare un'eccezione.  Tuttavia, questo esito non è garantito e per evitare di generare un'eccezione <xref:System.ObjectDisposedException?displayProperty=fullName>, è necessario evitare di chiamare <xref:System.IDisposable.Dispose%2A> più volte su un oggetto.  
  
## Regole correlate  
 [CA2000: Eliminare gli oggetti prima di perdere l'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare l'implementazione in modo che, a prescindere dal percorso del codice, <xref:System.IDisposable.Dispose%2A> venga chiamato una sola volta per oggetto.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Anche se è noto che il metodo <xref:System.IDisposable.Dispose%2A> può essere chiamato più volte senza rischi, in futuro l'implementazione potrebbe cambiare.  
  
## Esempio  
 Istruzioni `using` annidate \(`Using` in Visual Basic\) possono provocare violazioni dell'avviso CA2202.  Se la risorsa IDisposable dell'istruzione `using` interna annidata contiene la risorsa dell'istruzione `using` esterna, il metodo `Dispose` della risorsa annidata rilascia la risorsa contenuta.  Quando si verifica questa situazione, il metodo `Dispose` dell'istruzione `using` esterna tenta di eliminare la propria risorsa per una seconda volta.  
  
 Nell'esempio seguente, un oggetto <xref:System.IO.Stream> creato in un'istruzione using esterna viene rilasciato alla fine dell'istruzione using interna nel metodo Dispose dell'oggetto <xref:System.IO.StreamWriter> che contiene l'oggetto `stream`.  Alla fine dell'istruzione `using` esterna, l'oggetto `stream` viene rilasciato una seconda volta.  La seconda versione è una violazione di CA2202.  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## Esempio  
 Per risolvere questo problema utilizzare un blocco `try`\/`finally` anziché l'istruzione `using` esterna.  Nel blocco `finally`, verificare che la risorsa `stream` non sia null.  
  
```  
Stream stream = null;  
try  
{  
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        stream = null;  
        // Use the writer object...  
    }  
}  
finally  
{  
    if(stream != null)  
        stream.Dispose();  
}  
  
```  
  
## Vedere anche  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Modello Dispose](../Topic/Dispose%20Pattern.md)