---
title: "CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs | Microsoft Docs"
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
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
helpviewer_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## Causa  
 Una dichiarazione di metodo di platform invoke include un valore restituito o un parametro <xref:System.Boolean?displayProperty=fullName>, a cui tuttavia non viene applicato l'attributo <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>.  
  
## Descrizione della regola  
 Un metodo di platform invoke accede al codice non gestito e viene definito mediante la parola chiave `Declare` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o mediante <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  <xref:System.Runtime.InteropServices.MarshalAsAttribute> specifica il comportamento di marshalling utilizzato per convertire i tipi di dati tra codice gestito e non gestito.  Molti tipi di dati semplici quali <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, offrono una rappresentazione singola in codice non gestito e non richiedono la specifica del relativo comportamento di marshalling. Common Language Runtime fornisce automaticamente il funzionamento corretto.  
  
 Per il tipo di dati <xref:System.Boolean> sono disponibili più rappresentazioni nel codice non gestito.  Quando <xref:System.Runtime.InteropServices.MarshalAsAttribute> non è specificato, il comportamento di marshalling predefinito per il tipo di dati <xref:System.Boolean> è <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>.  Si tratta di un Integer a 32 bit, che non è appropriato in tutte le circostante.  La rappresentazione booleana richiesta dal metodo non gestito dovrebbe essere determinata e messa in corrispondenza con l'oggetto <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> appropriato.  UnmanagedType.Bool è il tipo BOOL Win32, che è sempre pari a 4 byte.  UnmanagedType.U1 dovrebbe essere utilizzato per C\+\+ `bool` o altri tipi a 1 byte.  Per ulteriori informazioni, vedere [Default Marshaling for Boolean Types](http://msdn.microsoft.com/it-it/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, applicare <xref:System.Runtime.InteropServices.MarshalAsAttribute> al valore restituito o al parametro <xref:System.Boolean>.  Impostare il valore dell'attributo sull'oggetto <xref:System.Runtime.InteropServices.UnmanagedType> appropriato.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Anche se il comportamento di marshalling predefinito è appropriato, il codice viene gestito più facilmente quando il comportamento è specificato in modo esplicito.  
  
## Esempio  
 Nell'esempio riportato di seguito sono illustrati due metodi di platform invoke contrassegnati dagli attributi <xref:System.Runtime.InteropServices.MarshalAsAttribute> appropriati.  
  
 [!code-cs[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## Regole correlate  
 [CA1901: Le dichiarazioni P\/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101: Specificare il marshalling per gli argomenti di stringa P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## Vedere anche  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/it-it/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)