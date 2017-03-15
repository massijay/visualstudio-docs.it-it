---
title: "How to: Split a Class into Partial Classes (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer, partial classes"
  - "partial classes, Class Designer"
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# How to: Split a Class into Partial Classes (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile dividere la dichiarazione di una classe o struttura tra diverse dichiarazioni utilizzando la parola chiave `Partial` in Visual Basic o la parola chiave `partial` in Visual C\#.  È possibile utilizzare tutte le dichiarazioni parziali desiderate, in tutti i diversi file di origine desiderati o in uno soltanto.  Tutte le dichiarazioni, tuttavia, devono trovarsi in un assembly e in uno spazio dei nomi identici.  
  
 Le classi parziali sono utili in diverse situazioni.  Ad esempio, quando si lavora su progetti di grandi dimensioni, la separazione di una classe in più file ne consente l'utilizzo contemporaneo da parte di più programmatori.  Quando si utilizza codice generato da Visual Studio, è possibile modificare la classe senza dover ricreare il file di origine  \(gli esempi di codice generato da Visual Studio includono codice wrapper di servizi Web e Windows Form\). È pertanto possibile creare codice che utilizzi classi generate automaticamente senza dover modificare il file creato da Visual Studio.  
  
 Sono disponibili due tipi di metodi parziali.  Tali metodi vengono denominati dichiarazione e implementazione sia in Visual C\# sia in Visual Basic.  
  
 Progettazione classi supporta classi e metodi parziali.  La forma del tipo nel diagramma classi si riferisce a un singolo percorso della dichiarazione per la classe parziale.  Se la classe parziale viene definita in più file, è possibile specificare il percorso della dichiarazione utilizzato da Progettazione classi impostando la proprietà **Percorso nuovi membri** nella finestra **Proprietà**.  In altre parole, quando si fa doppio clic sulla forma di una classe, Progettazione classi passa al file di origine che contiene la dichiarazione di classe identificata dalla proprietà **Percorso nuovi membri**.  Quando si fa doppio clic su un metodo parziale nella forma di una classe, Progettazione classi passa alla dichiarazione del metodo parziale.  Anche la proprietà **Nome file** nella finestra **Proprietà** si riferisce al percorso della dichiarazione.  Per le classi parziali, **Nome file** elenca tutti i file che contengono codice di dichiarazione e di implementazione per tali classi.  Per i metodi parziali, invece, **Nome file** elenca solo il file che contiene la dichiarazione del metodo parziale.  
  
 Negli esempi riportati di seguito la definizione della classe `Employee` viene suddivisa in due dichiarazioni, ciascuna delle quali definisce una diversa routine.  Le due definizioni parziali contenute negli esempi possono trovarsi in un unico file di origine o in due file di origine diversi.  
  
> [!NOTE]
>  In Visual Basic vengono utilizzate definizioni di classi parziali per separare il codice generato da Visual Studio da quello creato dall'utente.  Il codice viene separato in file di origine distinti.  In **Progettazione Windows Form**, ad esempio, vengono definite classi parziali per controlli come `Form`.  In questi controlli il codice generato non deve essere modificato.  
  
 Per ulteriori informazioni sui tipi parziali in Visual Basic, vedere [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## Esempio  
 Per suddividere una definizione di classe in Visual Basic, utilizzare la parola chiave `Partial`, come mostrato nell'esempio riportato di seguito.  
  
```vb#  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## Esempio  
 Per suddividere una definizione di classe in Visual C\#, utilizzare la parola chiave `partial`, come mostrato nell'esempio riportato di seguito.  
  
```c#  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## Vedere anche  
 [Classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [parziale \(Tipo\)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [parziale \(Metodo\) \(Riferimenti per C\#\)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)