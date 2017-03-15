---
title: "Utilizzo di classi Assert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert (classi)"
  - "Assert (istruzioni)"
  - "unit test, Assert (istruzioni)"
  - "unit test, Assert (classi)"
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 27
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 27
---
# Utilizzo di classi Assert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le classi Assert dello spazio dei nomi UnitTestingFramework permettono di verificare funzionalità specifiche.  Un metodo di unit test verifica il codice di un metodo nel codice di sviluppo, ma segnala la correttezza del comportamento del codice soltanto se sono state incluse istruzioni Assert.  
  
## Tipi di classi Assert  
 Lo spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UnitTesting> fornisce vari tipi di classi Assert:  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 Nel metodo di test è possibile chiamare un numero qualsiasi di metodi della classe Assert, ad esempio Assert.AreEqual\(\).  Nella classe Assert sono disponibili numerosi metodi tra cui scegliere e molti di questi metodi hanno vari overload.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 La classe CollectionAssert permette di confrontare le raccolte di oggetti e di verificare lo stato di una o più raccolte.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Utilizzare la classe StringAssert per confrontare le stringhe.  Questa classe contiene una varietà di metodi utili, come StringAssert.Contains, StringAssert.Matches e StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 L'eccezione AssertFailedException viene generata ogni volta che un test ha esito negativo.  Un test ha esito negativo in caso di timeout, se viene generata un'eccezione o se contiene un'istruzione Assert che produce un risultato Non riuscito.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 L'eccezione AssertInconclusiveException viene generata ogni volta che un test produce un risultato Senza risultati.  In genere un'istruzione Assert.Inconclusive viene aggiunta a un test su cui si sta ancora lavorando per indicare che non è ancora pronto per l'esecuzione.  
  
> [!NOTE]
>  Una strategia alternativa consiste nel contrassegnare con l'attributo Ignora un test che non è pronto per l'esecuzione.  Vi è tuttavia uno svantaggio: non è semplice generare un report sul numero di test rimasti da implementare.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 Se si scrive una nuova classe di eccezione Assert, ereditando tale classe dalla classe base UnitTestAssertException, viene semplificata l'identificazione dell'eccezione come errore di asserzione anziché come eccezione imprevista generata dal test o dal codice di produzione.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Decorare un metodo di test con l'attributo ExpectedExceptionAttribute quando si desidera che con il metodo di test venga verificato se un'eccezione che si prevede venga generata da un metodo nel codice di sviluppo non sia invece generata in tale metodo.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Creating and Running Unit Tests for Existing Code](http://msdn.microsoft.com/it-it/e8370b93-085b-41c9-8dec-655bd886f173)