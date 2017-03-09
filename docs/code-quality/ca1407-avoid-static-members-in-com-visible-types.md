---
title: "CA1407: Evitare i membri statici nei tipi visibili a COM | Microsoft Docs"
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
  - "CA1407"
  - "AvoidStaticMembersInComVisibleTypes"
helpviewer_keywords: 
  - "CA1407"
  - "AvoidStaticMembersInComVisibleTypes"
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1407: Evitare i membri statici nei tipi visibili a COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidStaticMembersInComVisibleTypes|  
|CheckId|CA1407|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo specificatamente contrassegnato come visibile a COM \(Component Object Model\) contiene un metodo `public` `static`.  
  
## Descrizione della regola  
 COM non supporta i metodi `static`.  
  
 Questa regola ignora le funzioni di accesso a proprietà ed eventi, i metodi di overload degli operatori o i metodi contrassegnati con l'attributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
 Per impostazione predefinita, i seguenti elementi sono visibili a COM: assembly, tipi pubblici, membri di istanza pubblici in tipi pubblici e tutti i membri di tipi di valore pubblici.  
  
 Per il verificarsi di questa regola, è necessario che un oggetto <xref:System.Runtime.InteropServices.ComVisibleAttribute> a livello di assembly sia impostato su `false` e che l'oggetto <xref:System.Runtime.InteropServices.ComVisibleAttribute> relativo a classe sia impostato su `true` come illustrato nel codice seguente.  
  
```c#  
using System;  
using System.Runtime.InteropServices;   
  
[assembly: ComVisible(false)]   
namespace Samples  
{      
    [ComVisible(true)]  
    public class MyClass  
    {  
        public static void DoSomething()  
        {  
        }  
    }  
}  
```  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la progettazione in modo da utilizzare un metodo di istanza che fornisca la stessa funzionalità del metodo `static`.  
  
## Esclusione di avvisi  
 È sicuro escludere un avviso da questa regola se un client COM non deve accedere alla funzionalità fornita dal metodo `static`.  
  
## Esempio di violazione  
  
### Descrizione  
 Nell'esempio riportato di seguito viene dichiarato un metodo `static` che viola questa regola.  
  
### Codice  
 [!code-cs[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### Commenti  
 In questo esempio non è possibile chiamare il metodo **Book.FromPages** da COM.  
  
## Correzione di esempio  
  
### Descrizione  
 Per correggere la violazione nell'esempio precedente, è possibile impostare il metodo su un metodo di istanza. In questo caso specifico sarebbe tuttavia inutile.  Una soluzione migliore consiste nell'applicare in modo esplicito `ComVisible(false)` al metodo per spiegare chiaramente agli altri sviluppatori che il metodo non è visibile da COM.  
  
 Nell'esempio riportato di seguito viene applicato <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> al metodo.  
  
### Codice  
 [!code-cs[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## Regole correlate  
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## Vedere anche  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)