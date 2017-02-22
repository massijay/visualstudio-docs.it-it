---
title: "Supporto del debug in modalit&#224; mista solo quando si utilizza Microsoft .NET Framework 2.0 o 3.0 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_to_old"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Supporto del debug in modalit&#224; mista solo quando si utilizza Microsoft .NET Framework 2.0 o 3.0
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le versioni di Microsoft .NET Framework precedenti alla 2.0 non forniscono alcun supporto per il debug in modalità mista di processi a 64 bit.  Ciò significa che non è possibile passare dal codice gestito al codice nativo o viceversa durante l'esecuzione del debug.  
  
 Per aggirare il problema è possibile:  
  
-   Aggiornare il progetto per utilizzare Microsoft .NET Framework 2.0 o 3.0.  
  
-   Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.  
  
-   Eseguire il debug del codice misto come processo a 32 bit, come descritto nelle procedure che seguono.  
  
### Per modificare il sistema operativo a 32 bit \(Visual Basic o C\#\)  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi fare clic su **Proprietà** nel menu di scelta rapida.  
  
2.  Nella pagina delle proprietà fare clic sulla scheda **Compilazione** o **Debug**.  
  
3.  Fare clic su **Piattaforma**, quindi selezionare **x86** dall'elenco delle piattaforme.  
  
     Per impostazione predefinita, i compilatori di Visual Basic e C\# producono codice eseguibile in qualsiasi CPU.  In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit.  Per l'esecuzione in un processo a 32 bit, è necessario scegliere **Win32** anziché **AnyCPU**.  
  
### Per modificare il sistema operativo a 32 bit \(C\/C\+\+\)  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi fare clic su **Proprietà** nel menu di scelta rapida.  
  
     Nella pagina delle proprietà fare clic su **Piattaforma**, quindi selezionare **Win32** dall'elenco delle piattaforme.  
  
### Per correggere l'errore  
  
-   Vedere [Setting Up SQL Debugging](http://msdn.microsoft.com/it-it/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## Vedere anche  
 [Eseguire il debug di applicazioni a 64 bit](../debugger/debug-64-bit-applications.md)