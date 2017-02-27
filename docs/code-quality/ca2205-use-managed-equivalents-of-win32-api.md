---
title: "CA2205: Utilizzare equivalenti gestiti dell&#39;API Win32 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseManagedEquivalentsOfWin32Api"
  - "CA2205"
helpviewer_keywords: 
  - "CA2205"
  - "UseManagedEquivalentsOfWin32Api"
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2205: Utilizzare equivalenti gestiti dell&#39;API Win32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Viene definito un metodo di platform invoke e nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] è presente un metodo con la funzionalità equivalente.  
  
## Descrizione della regola  
 Un metodo di platform invoke viene utilizzato per chiamare una funzione DLL non gestita e viene definito mediante l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> o la parola chiave `Declare` in Visual Basic.  Un metodo di platform invoke definito in modo errato può causare eccezioni in fase di esecuzione come conseguenza di problemi quali funzione con nome non corretto, mapping errato dei tipi di dati di parametri e valori restituiti oppure specifiche di campi errate, ad esempio la convenzione di chiamata e il set di caratteri.  Se disponibile, è in genere più semplice e presenta minori possibilità di errore chiamare il metodo gestito equivalente anziché definire e chiamare direttamente il metodo non gestito.  La chiamata a un metodo di platform invoke può inoltre causare ulteriori problemi di sicurezza che dovranno essere risolti.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire la chiamata alla funzione non gestita con una chiamata al relativo equivalente gestito.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola se il metodo di sostituzione consigliato non fornisce la funzionalità desiderata.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrata una definizione di metodo di platform invoke che viola la regola.  Vengono inoltre illustrate le chiamate al metodo di platform invoke e al metodo gestito equivalente.  
  
 [!code-cs[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## Regole correlate  
 [CA1404: Chiamare GetLastError immediatamente dopo P\/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060: Spostare i P\/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: I punti di ingresso P\/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: I P\/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Specificare il marshalling per gli argomenti di stringa P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)