---
title: "Procedura: impostare il nome di un thread in codice gestito | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug [Visual Studio], thread"
  - "nomi di thread"
  - "Thread.Name (proprietà)"
  - "threading [Visual Studio], nomi"
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Procedura: impostare il nome di un thread in codice gestito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La denominazione dei thread è possibile in tutte le edizioni di Visual Studio.  Tale denominazione consente di tenere traccia dei thread nella finestra **Thread**.  Poiché la finestra **Thread** non è disponibile nelle versioni di Visual Studio Express Edition, la denominazione dei thread è di poca utilità in tali versioni.  
  
 Per impostare il nome di un thread in codice gestito, usare la proprietà <xref:System.Threading.Thread.Name%2A>.  
  
## Esempio  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: impostare il nome di un thread in codice nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)