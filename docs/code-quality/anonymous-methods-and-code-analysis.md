---
title: "Metodi anonimi e analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "metodi anonimi, analisi codice"
  - "analisi codice, metodi anonimi"
  - "metodi, anonimi"
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Metodi anonimi e analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un *metodo anonimo* è un metodo privo di nome.  I metodi anonimi vengono usati il più delle volte per passare un blocco di codice come parametro di delegato.  
  
 In questo argomento viene illustrata la gestione nell'analisi del codice degli avvisi e della metrica associati a metodi anonimi.  
  
## Metodi anonimi dichiarati all'interno di un membro  
 Le metriche e gli avvisi per un metodo anonimo dichiarato in un membro, ad esempio un metodo o una funzione di accesso, vengono associati al membro che dichiara il metodo.  Non vengono quindi associati al membro che chiama il metodo.  
  
 Nella classe seguente, ad esempio, qualsiasi avviso trovato nella dichiarazione di **anonymousMethod**, deve essere generato in base a **Method1** e non a **Method2**.  
  
```vb#  
  
        Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As  Integer) value > 5  
        Method2(anonymousMethod)  
    End Sub Sub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    void Method1()  
    {  
        Delegate anonymousMethod = delegate()   
        {   
          Console.WriteLine("");   
        }  
        Method2(anonymousMethod);  
    }  
  
    void Method2(Delegate anonymousMethod)  
    {  
        anonymousMethod();  
    }  
}  
```  
  
## Metodi anonimi inline  
 Gli avvisi e la metrica per un metodo anonimo, dichiarati come assegnazione inline a un campo, vengono associati al costruttore.  Se il campo viene dichiarato come `static` \(`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), gli avvisi e la metrica vengono associati al costruttore di classe; in caso contrario, vengono associati al costruttore di istanza.  
  
 Nella classe seguente, ad esempio, qualsiasi avviso trovato nella dichiarazione di **anonymousMethod1** verrà generato in base al costruttore predefinito di **Class** generato in modo implicito.  Gli avvisi trovati in **anonymousMethod2**, invece, verranno applicati in base al costruttore di classe generato in modo implicito.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As     Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As      Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod1 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    static Delegate anonymousMethod2 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    void Method()  
    {  
       anonymousMethod1();  
       anonymousMethod2();  
    }  
}  
```  
  
 Una classe potrebbe contenere un metodo anonimo inline che assegna un valore a un campo che presenta più costruttori.  In questo caso, avvisi e metrica sono associati a tutti i costruttori a meno che quel costruttore sia concatenato a un altro costruttore nella stessa classe.  
  
 Nella classe seguente, ad esempio, qualsiasi avviso trovato nella dichiarazione di **anonymousMethod**, deve essere generato in base a **Class\(int\)** e **Class\(string\)**, ma non in base a **Class\(\)**.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
Sub New()  
    New(CStr(Nothing))  
End Sub Sub New(ByVal a As Integer)  
End Sub Sub New(ByVal a As String)  
End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    Class() : this((string)null)  
    {  
    }  
  
    Class(int a)  
    {  
    }  
  
    Class(string a)  
    {  
    }  
}  
```  
  
 Anche se imprevisto, questo comportamento deriva dal fatto che il compilatore restituisce un metodo univoco per ogni costruttore non concatenato a un altro costruttore.  A causa di questo comportamento, qualsiasi violazione che si verifica all'interno di **anonymousMethod** deve essere soppressa separatamente.  Ciò significa anche che se viene introdotto un nuovo costruttore, gli avvisi soppressi precedentemente in relazione a **Class\(int\)** e **Class\(string\)** devono essere soppressi anche in relazione al nuovo costruttore.  
  
 È possibile aggirare questo problema in due modi:  È possibile dichiarare **anonymousMethod** in un costruttore comune a cui vengono concatenati tutti i costruttori.  In alternativa, è possibile dichiararlo in un metodo di inizializzazione chiamato da tutti i costruttori.  
  
## Vedere anche  
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)