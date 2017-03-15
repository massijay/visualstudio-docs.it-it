---
title: "CA1062: Convalidare gli argomenti di metodi pubblici | Microsoft Docs"
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
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
  - "Validate arguments of public methods"
helpviewer_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1062: Convalidare gli argomenti di metodi pubblici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo visibile esternamente dereferenzia uno dei relativi argomenti di riferimento senza verificare se tale argomento è `null` \(`Nothing` in Visual Basic\).  
  
## Descrizione della regola  
 È necessario che tutti gli argomenti di riferimento che sono passati a metodi visibili esternamente vengano sottoposti a verifica per accertarsi che non corrispondano a valori `null`.  Se possibile, quando l'argomento è `null`, verrà generata un'eccezione <xref:System.ArgumentNullException>.  
  
 Se è possibile chiamare un metodo da un assembly sconosciuto perché viene dichiarato pubblico o protetto, è necessario convalidare tutti i parametri del metodo.  Se il metodo viene progettato per essere chiamato solo dagli assembly noti, è necessario rendere il metodo interno e applicare l'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> all'assembly che contiene il metodo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, convalidare ciascun argomento di riferimento per accertarsi che non sia `null`.  
  
## Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se il parametro dereferenziato è stato convalidato da un'altra chiamata al metodo nella funzione.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che viola la regola e un metodo che la soddisfa.  
  
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_1.vb)]  
  
## Esempio  
 In [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], questa regola non consente di rilevare che i parametri vengono passati a un altro metodo che esegue la convalida.  
  
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_2.vb)]  
  
## Esempio  
 Costruttori di copia che popolano campo o proprietà che sono oggetti di riferimento possono violare anche la regola CA1062.  La violazione si verifica perché l'oggetto copiato che viene passato al costruttore di copia potrebbe essere `null` \(`Nothing` in Visual Basic\).  Per risolvere la violazione, utilizzare un metodo statico \(Condiviso in Visual Basic\) per controllare che l'oggetto copiato non è null.  
  
 Nel seguente esempio di classe `Person`, l'oggetto `other` che viene passato al costruttore di copia `Person` potrebbe essere `null`.  
  
```  
  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor CA1062 fires because other is dereferenced  
    // without being checked for null  
    public Person(Person other)  
        : this(other.Name, other.Age)  
    {  
    }  
}  
  
```  
  
## Esempio  
 Nel seguente esempio di `Person` modificato, per l'oggetto `other` passato al costruttore di copia, viene in primo luogo controllata la presenza di valori null nel metodo `PassThroughNonNull`.  
  
```  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor  
    public Person(Person other)  
        : this(PassThroughNonNull(other).Name,   
          PassThroughNonNull(other).Age)  
    {   
    }  
  
    // Null check method  
    private static Person PassThroughNonNull(Person person)  
    {  
        if (person == null)  
            throw new ArgumentNullException("person");  
        return person;  
    }  
}  
  
```