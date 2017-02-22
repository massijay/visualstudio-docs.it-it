---
title: "Il debug in modalit&#224; mista per i processi IA64 non &#232; supportato. | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_ia64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Il debug in modalit&#224; mista per i processi IA64 non &#232; supportato.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio non supporta debug in modalità mista di codice gestito e nativo nei processi IA64.  Questo significa che non è possibile passare dal codice gestito al codice nativo, o viceversa, durante l'esecuzione del debug.  
  
### Soluzioni  
  
-   Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.  
  
     \-oppure\-  
  
     Eseguire il debug del codice misto come processo a 32 bit, come descritto nelle procedure che seguono.  
  
### Per impostare la piattaforma su 32 bit \(Visual Basic o C\#\)  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi fare clic su **Proprietà** nel menu di scelta rapida.  
  
2.  Nella pagina delle proprietà fare clic sulla scheda **Compilazione** o **Debug**.  
  
3.  Fare clic su **Piattaforma** e selezionare x86 dall'elenco di piattaforme.  
  
     Per impostazione predefinita, i compilatori Visual Basic e C\# producono codice eseguibile in qualsiasi CPU.  In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit.  Per l'esecuzione in un processo a 32 bit, è necessario scegliere **Win32** anziché **AnyCPU**.  
  
### Per impostare la piattaforma su 32 bit \(C\/C\+\+\)  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi fare clic su **Proprietà** nel menu di scelta rapida.  
  
2.  Nelle pagine delle proprietà fare clic su **Piattaforma** e selezionare Win32 dall'elenco di piattaforme.  
  
## Vedere anche  
 [Eseguire il debug di applicazioni a 64 bit](../debugger/debug-64-bit-applications.md)