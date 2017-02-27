---
title: "Risoluzione dei problemi relativi alla metrica codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 4
---
# Risoluzione dei problemi relativi alla metrica codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile che durante la raccolta di metrica codice si verifichino alcuni dei problemi seguenti:  
  
-   [Modifiche nei calcoli di complessità del codice di Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Modifiche nei calcoli di complessità del codice di Visual Studio 2010  
 Per la stessa funzione è possibile che la metrica di complessità del codice calcolata in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] sia diversa dalla metrica calcolata da versioni precedenti di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] per le situazioni seguenti:  
  
-   La funzione contiene uno o più blocchi catch.  Nelle versioni precedenti di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] i blocchi catch non sono inclusi nel calcolo.  In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] la complessità di ogni blocco catch viene aggiunta alla complessità della funzione.  
  
-   La funzione contiene un'istruzione switch \(Select Case in VB\).  le differenze del compilatore tra [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e le versioni precedenti può generare codice MSIL diverso per alcune istruzioni switch che contengono casi di passaggio.  
  
## Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)