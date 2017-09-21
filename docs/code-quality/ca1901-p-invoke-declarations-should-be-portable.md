---
title: "CA1901: Le dichiarazioni P/Invoke devono essere portabili | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
helpviewer_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1901: Le dichiarazioni P/Invoke devono essere portabili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Categoria|Microsoft.Portability|  
|Breaking Change|Sostanziale \- Se P\/Invoke è visibile all'esterno dell'assembly.  Non sostanziale \- Se P\/Invoke non è visibile all'esterno dell'assembly.|  
  
## Causa  
 La regola valuta la dimensione di ciascun parametro e il valore restituito di P\/Invoke e verifica che la relativa dimensione a seguito del marshalling a codice non gestito su piattaforme a 32 e 64 bit sia corretta.  La violazione più comune di questa regola consiste nel passare un Integer a dimensione fissa laddove è necessaria una variabile della dimensione del puntatore dipendente dalla piattaforma.  
  
## Descrizione della regola  
 Questa regola si verifica quando viene violato ciascuno dei seguenti scenari:  
  
-   Il valore restituito o il parametro è tipizzato come numero intero a dimensione fissa quando deve essere tipizzato come `IntPtr`.  
  
-   Il valore restituito o il parametro è tipizzato come `IntPtr` quando deve essere tipizzato come numero intero a dimensione fissa.  
  
## Come correggere le violazioni  
 È possibile correggere la violazione utilizzando `IntPtr` o `UIntPtr` invece di `Int32` o `UInt32` per rappresentare gli handle.  
  
## Esclusione di avvisi  
 Non escludere tale avviso.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrata una violazione di questa regola.  
  
```c#  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 In questo esempio, il parametro `nIconIndex` è dichiarato come un `IntPtr`, che è grande 4 byte in una piattaforma a 32 bit e a 8 byte in una piattaforma a 64 bit.  Nella dichiarazione non gestita che segue, è possibile vedere che `nIconIndex` è un unsigned integer di 4\-byte su tutte le piattaforme.  
  
```c#  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## Esempio  
 Per correggere la violazione, modificare la dichiarazione come segue:  
  
```c#  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## Vedere anche  
 [Avvisi di portabilità](../code-quality/portability-warnings.md)