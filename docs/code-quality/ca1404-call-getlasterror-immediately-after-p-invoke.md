---
title: "CA1404: Chiamare GetLastError immediatamente dopo P/Invoke | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
helpviewer_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1404: Chiamare GetLastError immediatamente dopo P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Viene effettuata una chiamata al metodo <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> o alla funzione `GetLastError` Win32 equivalente e la chiamata immediatamente precedente non è una chiamata a un metodo platform invoke.  
  
## Descrizione della regola  
 Un metodo di platform invoke accede al codice non gestito e viene definito mediante la parola chiave `Declare` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o mediante l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  In genere, in caso di errore, le funzioni non gestite chiamano la funzione `SetLastError` Win32 per impostare un codice di errore associato all'errore.  Il chiamante della funzione non riuscita chiama la funzione `GetLastError` Win32 per recuperare il codice di errore e determinare la causa dell'errore.  Il codice errore viene mantenuto per ogni singolo thread e viene sovrascritto dalla successiva chiamata a `SetLastError`.  Dopo una chiamata a un metodo di platform invoke non riuscito, il codice gestito può recuperare il codice di errore chiamando il metodo <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>.  Poiché il codice di errore può essere sovrascritto da chiamate interne da altri metodi della libreria di classi gestite, il metodo `GetLastError` o <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> deve essere chiamato immediatamente dopo la chiamata al metodo di platform invoke.  
  
 La regola ignora le chiamate ai seguenti membri gestiti quando si verificano tra la chiamata al metodo di platform invoke e la chiamata a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>.  Questi membri non modificano il codice di errore e sono utili per determinare la riuscita di determinate chiamate a metodi di platform invoke.  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, spostare la chiamata a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> in modo che segua immediatamente la chiamata al metodo di platform invoke.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il codice tra la chiamata al metodo P\/Invoke e la chiamata al metodo <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> non può causare in modo esplicito o implicito la modifica del codice di errore.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che viola la regola e un metodo che la soddisfa.  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-cs[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## Regole correlate  
 [CA1060: Spostare i P\/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: I punti di ingresso P\/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: I P\/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Specificare il marshalling per gli argomenti di stringa P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205: Utilizzare equivalenti gestiti dell'API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)