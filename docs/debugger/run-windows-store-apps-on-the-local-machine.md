---
title: "Eseguire applicazioni Windows Store in un computer locale | Microsoft Docs"
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
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Eseguire applicazioni Windows Store in un computer locale
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Si applica solo a Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Per eseguire il debug, test o analisi delle prestazioni su un'app Windows Store, puoi eseguire l'app sullo stesso computer che ospita Visual Studio.  Se lo schermo del dispositivo è abilitato per il tocco, puoi verificare la funzionalità completa dell'app, altrimenti dovrai limitarti ai movimenti con il mouse e la tastiera.  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 Puoi acquisire informazioni su:  
  
 [Come eseguire l'app su un computer locale](#BKMK_How_to_run_on_a_local_machine)  
  
 [Come passare tra un'app Windows Store e Visual Studio su un solo monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> Come eseguire l'app su un computer locale  
 Per eseguire l'app sul computer locale, seleziona **Computer locale** nell'elenco a discesa accanto al pulsante Avvia debug sulla barra degli strumenti **Standard** del debugger.  
  
 ![Effettuare l'esecuzione nel computer locale](../debugger/media/vsrun_f5_local.png "VSRUN\_F5\_Local")  
  
 Se la barra degli strumenti **Standard** non è visualizzata, fai clic sul menu **Visualizza**, scegli **Barre degli strumenti** e poi fai clic su **Standard**.  
  
 La scelta adottata nell'elenco a discesa viene mantenuta nel file delle proprietà del progetto e diventa la destinazione di esecuzione predefinita.  
  
 Puoi anche impostare la destinazione di esecuzione direttamente nel file delle proprietà del progetto.  Fai clic con il pulsante destro del mouse sul nome del progetto in **Esplora soluzioni** e scegli **Proprietà**.  Effettua una delle seguenti operazioni:  
  
-   In progetti C\# e Visual Basic fai clic su **Debug** e seleziona **Computer locale** nell'elenco a discesa **Dispositivo di destinazione**.  
  
     ![Pagina delle proprietà del progetto C&#35; e Visual Basic](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN\_CS\_VB\_ProjProp\_Local")  
  
-   In progetti C\+\+ e JavaScript espandi il nodo **Proprietà di configurazione**, fai clic su **Debug** e seleziona **Debugger locale** nell'elenco **Debugger da avviare**.  
  
     ![Pagina delle proprietà del progetto C&#43;&#43; e JavaScript](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN\_CPP\_JS\_ProjProp\_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Come passare tra un'app Windows Store e Visual Studio su un solo monitor  
 **Per passare da un'istanza in esecuzione di un'app Windows Store a Visual Studio**  
  
 Quando esegui un'app Windows Store su un computer locale e usi un solo monitor, potresti voler tornare a Visual Studio lasciando in esecuzione l'app.  L'app potrebbe essere in uno stato che non può essere raggiunto da un punto di interruzione, ad esempio potrebbe essere in attesa di un evento o inclusa in un ciclo lungo o infinito.  Per tornare a Visual Studio, premi ALT\+TAB.