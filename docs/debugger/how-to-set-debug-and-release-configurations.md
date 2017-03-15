---
title: "Procedura: impostare le configurazioni di debug e rilascio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.builds"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "configurazioni di compilazione, debug"
  - "configurazioni di compilazione, rilascio"
  - "configurazioni, rilascio"
  - "compilazioni di debug"
  - "compilazioni di debug, modifica delle impostazioni di configurazione"
  - "compilazioni di debug, passaggio alla build di rilascio"
  - "configurazioni di debug"
  - "debug [Visual Studio], configurazioni di debug"
  - "debug [Visual Studio], configurazioni di rilascio"
  - "progetti [Visual Studio], configurazioni di debug"
  - "progetti [Visual Studio], configurazioni di rilascio"
  - "build di rilascio, modifica delle impostazioni"
  - "build di rilascio, passaggio alla build di debug"
  - "Visual Basic (progetti), build di debug e rilascio"
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Procedura: impostare le configurazioni di debug e rilascio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Progetti di Visual Studio installata versione separata e configurazioni per il programma di debug.  Come indicato dai nomi, la versione di debug viene compilata per eseguire il debug, mentre quella di rilascio viene compilata per la distribuzione finale.  
  
 La configurazione di debug del programma è compilata con le informazioni complete di debug sui simboli e senza ottimizzazione.  L'ottimizzazione rende più difficile il debug perché la relazione tra il codice sorgente e le istruzioni generate è più complessa.  
  
 La configurazione di rilascio del programma non contiene alcuna informazione di debug sui simboli ed è perfettamente ottimizzata.  Le informazioni di debug possono essere generate in file PDB, in base alle opzioni del compilatore utilizzate.  La creazione di file PDB può essere molto utile se successivamente sarà necessario eseguire il debug della versione di rilascio.  
  
 Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
 È possibile modificare la configurazione di compilazione dal **Build** menu nella barra degli strumenti o nelle pagine di proprietà del progetto.  Pagine delle proprietà del progetto sono specifici del linguaggio.  La procedura riportata di seguito viene illustrato come modificare la configurazione di compilazione dal menu e barra degli strumenti.  Per ulteriori informazioni su come modificare la configurazione di compilazione nei progetti in linguaggi diversi, vedere la sezione Argomenti correlati.  
  
### Per modificare la configurazione di compilazione  
  
1.  Dal menu Compila: fare clic su **compilare \/ Configuration Manager**, quindi selezionare **Debug** o **versione**.  
  
2.  Sulla barra degli strumenti selezionare **Debug** o **Release**nella caselle di riepilogo **Configurazione soluzione**  
  
     ![configurazione di compilazione per la barra degli strumenti](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Questa procedura guidata non è disponibile nelle edizioni Express.  È possibile utilizzare le voci di menu **Compila soluzione F6** e **Avvia debug F5** per scegliere la configurazione.  
  
## Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)   
 [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Impostazioni di progetto per le configurazioni di debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)   
 [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e)