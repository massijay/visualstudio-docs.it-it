---
title: "Debug gestito: impostazioni consigliate delle propriet&#224; | Microsoft Docs"
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
  - "debug [Visual Studio], gestito"
  - "debug di codice gestito, impostazioni di proprietà consigliate"
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Debug gestito: impostazioni consigliate delle propriet&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determinate proprietà devono essere impostate nello stesso modo per tutti gli scenari di debug gestito.  
  
 Nelle tabelle riportate di seguito sono indicate le impostazioni consigliate delle proprietà.  
  
 Le impostazioni non specificate in queste tabelle possono variare in base al tipo di progetto gestito.  Ad esempio, la proprietà **Azione di avvio** verrà impostata in modo diverso in un progetto Windows Form e in un progetto [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
### Proprietà di configurazione disponibili nella scheda Compila \(C\#\) o Compila \(Visual Basic\)  
  
|**Nome proprietà**|**Impostazione**|  
|------------------------|----------------------|  
|**Definisci costante DEBUG**|C\# e F\#: selezionare la casella di controllo  per consentire all'applicazione di utilizzare la classe Debug.|  
|**Definisci costante TRACE**|C\# e F\#: selezionare la casella di controllo  per consentire all'applicazione di utilizzare la classe Trace.|  
|**Ottimizza codice**|C\#, F\# e Visual Basic: impostare su false.  L'esecuzione del debug di codice ottimizzato è più complessa perché le istruzioni generate non corrispondono direttamente al codice sorgente.  Se si nota un bug presente solo nel codice ottimizzato del programma, è possibile attivare questa impostazione, tenendo però presente che il codice riportato nella finestra **Disassembly** è generato da codice sorgente ottimizzato che potrebbe non corrispondere a quanto visualizzato nell'editor del codice.  Per eseguire il debug di codice ottimizzato, disattivare Just My Code. \(Vedere [Limitare l'esecuzione di istruzioni a Just My Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)\).<br /><br /> Per ulteriori informazioni, vedere [Impostazioni di progetto per le configurazioni di debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md) o [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Percorso output**|Impostare su bin\\Debug\\.|  
|**Opzioni di compilazione avanzate**|Solo Visual Basic.  Fare clic su **Avanzate** per impostare le proprietà avanzate descritte nella tabella riportata di seguito.|  
  
### Finestra di dialogo Impostazioni del compilatore avanzate  
  
|**Nome proprietà**|**Impostazione**|  
|------------------------|----------------------|  
|**Attiva ottimizzazioni**|Impostare su false per i motivi indicati nella descrizione dell'opzione **Ottimizza codice** nella tabella precedente.|  
|**Genera informazioni di debug**|Selezionare questa casella di controllo se si desidera che durante la compilazione venga impostato il flag \/DEBUG. In questo modo verranno generate le informazioni necessarie per semplificare il debug.|  
|**Definisci costante DEBUG**|Selezionare questa casella di controllo per definire la costante `DEBUG`, che consente all'applicazione di utilizzare la classe <xref:System.Diagnostics.Debug>.|  
|**Definisci costante TRACE**|Selezionare questa casella di controllo per definire la costante `TRACE`, che consente all'applicazione di utilizzare la classe <xref:System.Diagnostics.Trace>.|  
  
## Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto C\#, F\# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)