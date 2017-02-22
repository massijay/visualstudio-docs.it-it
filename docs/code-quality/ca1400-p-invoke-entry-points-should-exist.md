---
title: "CA1400: I punti di ingresso P/Invoke devono esistere | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1400"
  - "PInvokeEntryPointsShouldExist"
helpviewer_keywords: 
  - "PInvokeEntryPointsShouldExist"
  - "CA1400"
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1400: I punti di ingresso P/Invoke devono esistere
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeEntryPointsShouldExist|  
|CheckId|CA1400|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo pubblico o protetto è contrassegnato con l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  Non è possibile individuare la libreria non gestita né associare il metodo a una funzione nella libreria.  Se non è possibile trovare esattamente il nome del metodo come specificato, vengono cercate versioni ANSI o a caratteri estesi del metodo aggiungendo al relativo nome il suffisso "A" o "W".  Se non viene trovata alcuna corrispondenza, si tenta di individuare una funzione con il formato di denominazione \_\_stdcall \(\_MyMethod@12, dove 12 rappresenta la lunghezza degli argomenti\).  Se non viene trovata alcuna corrispondenza e il nome del metodo inizia con "\#", viene cercata la funzione come un riferimento ordinale anziché come riferimento del nome.  
  
## Descrizione della regola  
 Non è disponibile alcun controllo in fase di compilazione per assicurarsi che i metodi contrassegnati con <xref:System.Runtime.InteropServices.DllImportAttribute> siano presenti nella DLL non gestita a cui si fa riferimento.  Se nella libreria non è presente alcuna funzione con il nome specificato oppure gli argomenti del metodo non corrispondono agli argomenti della funzione, Common Language Runtime genera un'eccezione.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, correggere il metodo che presenta l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute>.  Assicurarsi che la libreria non gestita sia presente e si trovi nella stessa directory dell'assembly che contiene il metodo.  Se la libreria è presente e dispone di un riferimento corretto, verificare che il nome del metodo, il tipo restituito e la firma dell'argomento corrispondano alla funzione della libreria.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola se la libreria non gestita si trova nella stessa directory dell'assembly gestito che fa riferimento ad essa.  L'esclusione di un avviso da questa regola può essere sicura nel caso in cui non sia possibile individuare la libreria non gestita.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  Non è presente alcuna funzione denominata `DoSomethingUnmanaged` in kernel32.dll.  
  
 [!code-cs[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]  
  
## Vedere anche  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>