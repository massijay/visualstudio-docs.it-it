---
title: "CA1024: Utilizzare propriet&#224; dove appropriato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePropertiesWhereAppropriate"
  - "CA1024"
helpviewer_keywords: 
  - "CA1024"
  - "UsePropertiesWhereAppropriate"
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1024: Utilizzare propriet&#224; dove appropriato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo pubblico o protetto presenta un nome che inizia con `Get`, non accetta parametri e restituisce un valore diverso da una matrice.  
  
## Descrizione della regola  
 Nella maggior parte dei casi, le proprietà rappresentano dati e i metodi eseguono azioni.  Alle proprietà si accede come ai campi e sono pertanto più semplici da utilizzare.  Un metodo è un buon candidato per divenire una proprietà in presenza di una delle seguenti condizioni:  
  
-   Non accetta argomenti e restituisce le informazioni sullo stato di un oggetto.  
  
-   Accetta un solo argomento per impostare parte dello stato di un oggetto.  
  
 Le proprietà devono presentare un comportamento analogo ai campi. Se il metodo non può presentare un comportamento simile, non deve essere modificato in una proprietà.  I metodi sono preferibili alle proprietà nelle situazioni riportate di seguito:  
  
-   Il metodo esegue un'operazione che richiede molto tempo.  Il metodo è sensibilmente più lento rispetto al tempo richiesto per impostare o ottenere il valore di un campo.  
  
-   Il metodo esegue una conversione.  L'accesso a un campo non restituisce una versione convertita dei dati in esso archiviati.  
  
-   Il metodo Get presenta un effetto collaterale osservabile.  Il recupero del valore di un campo non produce alcun effetto secondario.  
  
-   L'ordine di esecuzione è importante.  L'impostazione del valore di un campo non si basa sull'esecuzione di altre operazioni.  
  
-   Se il metodo viene chiamato due volte consecutive, si otterranno risultati diversi.  
  
-   Il metodo è statico ma restituisce un oggetto che può essere modificato dal chiamante.  Il recupero del valore di un campo non consente al chiamante di modificare i dati archiviati nel campo.  
  
-   Il metodo restituisce una matrice.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il metodo in una proprietà.  
  
## Esclusione di avvisi  
 Eliminare un avviso da questa regola se il metodo soddisfa almeno uno dei criteri elencati in precedenza.  
  
## Controllo dell'espansione di proprietà nel debugger  
 Uno dei motivi per cui i programmatori tendono ad evitare l'utilizzo di proprietà è che non desiderano che il debugger le espanda automaticamente.  Ad esempio, la proprietà potrebbe prevedere l'allocazione di un oggetto di grandi dimensioni o la chiamata a P\/Invoke, ma potrebbe non avere effetti collaterali osservabili di alcun genere.  
  
 È possibile impedire che debugger espanda le proprietà automaticamente applicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>.  Nell'esempio seguente è mostrato questo attributo applicato a una proprietà di istanza.  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```c#  
  
        using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    public class TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## Esempio  
 Nell'esempio riportato di seguito sono contenuti diversi metodi che devono essere convertiti in proprietà e altri metodi che non devono essere convertiti perché non presentano comportamenti analoghi a campi.  
  
 [!code-cs[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]