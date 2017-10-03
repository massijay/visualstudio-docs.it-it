---
title: Risoluzione dei problemi di metrica codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: ea1e787c1d509123a650cf2bd20e5fa8bffd5b4e
ms.openlocfilehash: 9f3f41548412d84cd1219aae45b7c87ea5383de9
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="troubleshooting-code-metrics-issues"></a>Risoluzione dei problemi relativi alla metrica codice
Alcuni dei problemi seguenti possono verificarsi quando si raccolta metrica del codice:  
  
-   [Modifiche nei calcoli di complessità codice di Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Modifiche nei calcoli di complessità codice di Visual Studio 2010  
 Per la stessa funzione, la metrica di complessità del codice calcolata [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] può essere diversa dalla metrica calcolata da versioni precedenti di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] nelle situazioni seguenti:  
  
-   La funzione contiene uno o più blocchi catch. Nelle versioni precedenti di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], catch blocchi non sono inclusi nel calcolo. In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], si aggiunta la complessità di ogni blocco catch la complessità della funzione.  
  
-   La funzione contiene un'istruzione switch (Select Case in VB). Compilatore le differenze tra [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e versioni precedenti possono generare codice MSIL diverso per alcune istruzioni switch che contengono i casi di passaggio.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
