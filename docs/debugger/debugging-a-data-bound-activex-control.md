---
title: "Debug di un controllo ActiveX con associazione a dati | Microsoft Docs"
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
  - "controlli ActiveX, debug"
  - "controlli [Visual Studio], ActiveX"
  - "controlli con associazione a dati, ActiveX"
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Debug di un controllo ActiveX con associazione a dati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si sviluppa un controllo ActiveX che verrà associato a un controllo origine dati, è possibile creare un'applicazione contenitore e utilizzare il contenitore per eseguire il debug del controllo ActiveX.  
  
 È ad esempio possibile creare un'applicazione a finestre MFC e inserire nella finestra di dialogo il controllo con associazione a dati e un controllo origine dati.  Questa applicazione MFC può essere utilizzata per effettuare test in fase di esecuzione, nonché come eseguibile del contenitore per il debug del controllo ActiveX con associazione a dati.  
  
## Utilizzo di Test Container  
 Se si desidera un contenitore facilmente modificabile per il supporto di diverse interfacce sul controllo o sul contenitore, utilizzare ActiveX Test Container come eseguibile per la sessione di debug.  In ActiveX Test Container scegliere **Opzioni** dal menu **Contenitore** per attivare le diverse interfacce.  Per ulteriori informazioni, vedere [Test di proprietà ed eventi con Test Container](/visual-cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Per eseguire istruzione per istruzione il codice del contenitore durante il debug, utilizzare la versione di debug del contenitore oppure la versione di debug di ActiveX Control Test Container.  Per ulteriori informazioni, vedere [TSTCON Sample: ActiveX Control Test Container](http://msdn.microsoft.com/it-it/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## Vedere anche  
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Controlli ActiveX](/visual-cpp/mfc/activex-controls)