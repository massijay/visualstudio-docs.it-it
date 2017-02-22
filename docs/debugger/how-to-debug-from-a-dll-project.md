---
title: "Procedura: eseguire il debug da un progetto di DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "C++"
helpviewer_keywords: 
  - "debug [Visual Studio], DLL"
  - "debug di DLL"
  - "DLL (progetti), debug"
  - "DLL, debug di progetti"
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: eseguire il debug da un progetto di DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per avviare il debug di un progetto DLL, è necessario specificare l'applicazione chiamante nelle proprietà del progetto.  Il layout e il contenuto delle pagine delle proprietà di C\+\+ sono diversi da quelli delle pagine delle proprietà di C\# e Visual Basic.  
  
 Se una DLL gestita viene chiamata da codice nativo e si vuole eseguire il debug di entrambi, specificarlo nelle proprietà del progetto.  Per altre informazioni, vedere [Procedura: eseguire il debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
>  Non è possibile specificare un'applicazione chiamante esterna nelle edizioni Express di Visual Studio.  È necessario aggiungere un progetto eseguibile alla soluzione, impostarlo come progetto di avvio e chiamare i metodi nella DLL dal progetto eseguibile.  
  
### Per specificare l'applicazione chiamante in un progetto C\+\+  
  
1.  Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**.  Passare alla scheda **Debug**.  
  
2.  Assicurarsi che il campo **Configurazione** nella parte superiore della finestra sia impostato su **Debug**.  
  
3.  Passare a **Proprietà di configurazione \/ Debug**.  
  
4.  Nell'elenco **Debugger da avviare** scegliere **Debugger Windows locale** o **Debugger Windows remoto**.  
  
5.  Nella casella **Comando** o **Comando remoto** aggiungere il nome del percorso completo dell'applicazione.  
  
6.  Aggiungere tutti gli argomenti del programma necessari nella casella **Argomenti del comando**.  
  
### Per specificare l'applicazione chiamante in un progetto C\# o Visual Basic  
  
1.  Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**.  Passare alla scheda **Debug**.  
  
     Selezionare **Avvia programma esterno** e aggiungere il nome del percorso completo del programma da eseguire.  
  
     Se è necessario aggiungere gli argomenti della riga di comando del programma esterno, aggiungerli nel campo **Argomenti della riga di comando**.  
  
2.  È anche possibile chiamare un'applicazione sotto forma di URL.  Potrebbe essere necessario eseguire questa operazione se si esegue il debug di una DLL gestita usata da un'applicazione ASP.NET locale.  
  
     In **Azione di avvio** selezionare il pulsante di opzione **Avvia il browser con URL:** e specificare l'URL.  
  
### Per avviare il debug dal progetto DLL  
  
1.  Impostare i punti di interruzione necessari.  
  
2.  Avviare il debug \(premere F5, fare clic sulla freccia verde o fare clic su **Debug \/ Avvia debug**\).  
  
## Vedere anche  
 [Debug di progetti di DLL](../debugger/debugging-dll-projects.md)   
 [Impostazioni di progetto per le configurazioni di debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)