---
title: "Procedura: debug del codice sorgente di .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "debug, origine .NET Framework"
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: debug del codice sorgente di .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'ultima versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornisce nuove funzionalità per il debug di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Per eseguire il debug dell'origine [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], è necessario disporre dell'accesso ai simboli di debug per il codice.  Inoltre, è necessario attivare l'esecuzione dell'origine [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 È possibile attivare il download dei simboli e l'esecuzione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nella finestra di dialogo **Opzioni**.  Quando si attiva il download dei simboli, è possibile scegliere di scaricarli immediatamente o attivare solo l'opzione per eseguire il download successivamente.  Se non si esegue immediatamente il download, i simboli verranno scaricati la volta successiva che si avvia il debug dell'applicazione.  È possibile inoltre scaricarli manualmente dalla finestra **Moduli** o **Stack di chiamate**.  
  
### Per attivare il debug di origine di .NET Framework  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** fare clic sulla categoria **Debug**.  
  
3.  Nella casella **Generale** impostare **Abilita esecuzione di istruzioni origine .NET Framework**.  
  
    1.  Se Just My Code è attivato, viene visualizzata una finestra di dialogo con un avviso indicante che Just My Code è stato disabilitato.  Scegliere **OK**.  
  
    2.  Se il percorso della cache dei simboli non è impostato, viene visualizzata un'altra finestra di dialogo con un avviso indicante che è stato impostato il percorso predefinito della cache dei simboli.  Scegliere **OK**.  
  
4.  Nella categoria **Debug** fare clic su **Simboli**.  
  
5.  Se si desidera modificare il percorso della cache dei simboli:  
  
    1.  Aprire il nodo **Debug** nella casella a sinistra.  
  
    2.  Nel nodo **Debug** selezionare **Simboli**.  
  
    3.  Modificare il percorso in **Memorizza nella cache i simboli dai server di simboli in questa directory** o fare clic su **Sfoglia** per scegliere un percorso.  
  
6.  Per scaricare immediatamente simboli, fare clic su **Carica i simboli utilizzando i percorsi indicati sopra**.  
  
     Questo pulsante non è disponibile nella modalità progettazione.  
  
     Se non si sceglie di scaricare ora i simboli, questi ultimi verranno scaricati automaticamente al successivo avvio del debug del programma.  
  
7.  Scegliere **OK** per chiudere la finestra di dialogo **Opzioni**.  
  
### Per caricare simboli di Framework utilizzando la finestra Moduli  
  
1.  Nella finestra **Moduli**, fare clic con il pulsante destro del mouse sul modulo per il quale non sono caricati i simboli.  I moduli con i simboli caricati sono presenti nella colonna **Stato simboli**.  
  
2.  Scegliere **Carica simboli da** e fare clic su **Server dei simboli Microsoft** per scaricare i simboli dai server dei simboli pubblici Microsoft o scegliere **Percorso simboli** per caricare i simboli da una directory in cui precedentemente erano stati archiviati.  
  
### Per caricare simboli di Framework utilizzando la finestra Stack di chiamate  
  
1.  Nella finestra **Stack di chiamate**, fare clic con il pulsante destro del mouse sul frame per il quale non sono caricati i simboli.  Il frame verrà disattivato \(rappresentato in grigio\).  
  
2.  Scegliere **Carica simboli da**, quindi fare clic su **Server dei simboli Microsoft** o **Percorso simboli**.  
  
## Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)