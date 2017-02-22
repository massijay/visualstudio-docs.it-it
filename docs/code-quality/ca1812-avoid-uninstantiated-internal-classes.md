---
title: "CA1812: Evitare classi interne prive di istanze | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1812"
  - "AvoidUninstantiatedInternalClasses"
helpviewer_keywords: 
  - "AvoidUninstantiatedInternalClasses"
  - "CA1812"
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1812: Evitare classi interne prive di istanze
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUninstantiatedInternalClasses|  
|CheckId|CA1812|  
|Categoria|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un'istanza di un tipo a livello di assembly non viene creata dal codice nell'assembly.  
  
## Descrizione della regola  
 Mediante questa regola si tenta di individuare una chiamata a uno dei costruttori del tipo e viene segnalata una violazione se non viene trovata alcuna chiamata.  
  
 I tipi riportati di seguito non vengono esaminati da questa regola:  
  
-   Tipi di valore  
  
-   Tipi astratti  
  
-   Enumerazioni  
  
-   Delegati  
  
-   Tipi di matrice creati dal compilatore  
  
-   Tipi di cui non è possibile creare istanze e che definiscono soltanto metodi `static` \(`Shared` in Visual Basic\).  
  
 Se si applica <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> all'assembly che si sta analizzando, questa regola non si verificherà in qualsiasi costruttore contrassegnato come `internal` poiché non è possibile stabilire se un campo è utilizzato da un altro assembly `friend`.  
  
 Sebbene non sia possibile aggirare questa limitazione nell'analisi codice di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il codice FxCop autonomo esterno verrà eseguito sui costruttori interni, se ogni assembly `friend` è presente nell'analisi.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il tipo o aggiungere il codice che lo utilizza.  Se il tipo contiene solo metodi statici, aggiungere uno degli elementi riportati di seguito al tipo per impedire che il compilatore crei un costruttore di istanza pubblico predefinito:  
  
-   Costruttore privato per i tipi destinati a [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versioni 1.0 e 1.1.  
  
-   Il modificatore `static` \(`Shared` in Visual Basic\) per i tipi destinati a [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura.  Si consiglia di eliminare questo avviso nelle situazioni seguenti:  
  
-   La classe viene creata tramite metodi reflection ad associazione tardiva ad esempio <xref:System.Activator.CreateInstance?displayProperty=fullName>.  
  
-   La classe viene creata automaticamente dal runtime o da [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Ad esempio, classi che implementano <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> o <xref:System.Web.IHttpHandler?displayProperty=fullName>.  
  
-   La classe viene passata come un parametro di tipo generico con un nuovo vincolo.  Ad esempio, di seguito verrà attivata questa regola.  
  
    ```c#  
    internal class MyClass  
    {     
        public DoSomething()     
        {  
        }  
    }   
    public class MyGeneric<T> where T : new()  
    {  
        public T Create()  
        {  
            return new T();     
        }  
    }  
    // [...]   
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();  
    mc.Create();  
    ```  
  
 In queste situazioni si consiglia di eliminare l'avviso.  
  
## Regole correlate  
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1801: Rivedere i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)