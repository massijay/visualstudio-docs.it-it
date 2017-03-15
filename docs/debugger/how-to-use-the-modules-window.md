---
title: "Procedura: utilizzare la finestra Moduli | Microsoft Docs"
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
  - "vs.debug.modules"
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
  - "debugger, finestra Moduli"
  - "finestra Moduli"
  - "file eseguibili, visualizzazione durante il debug"
  - "debug [Visual Studio], visualizzazione moduli"
  - "DLL, visualizzazione durante il debug"
  - "moduli, visualizzazione"
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: utilizzare la finestra Moduli
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Questa funzionalità non è disponibile per il debug di script o SQL.  
  
 Nella finestra **Moduli** vengono elencati i file EXE e le DLL usati dal programma, unitamente a informazioni rilevanti per ognuno di essi.  
  
### Per visualizzare la finestra Moduli in modalità di interruzione o di esecuzione  
  
-   Scegliere **Finestre** dal menu **Debug**, quindi fare clic su **Moduli**.  
  
     Per impostazione predefinita, nella finestra **Moduli** i moduli sono ordinati in base all'ordine di caricamento.  È tuttavia possibile ordinare i moduli in base a qualsiasi colonna.  
  
### Per eseguire l'ordinamento in base a una colonna  
  
-   Fare clic sul pulsante nella parte superiore della colonna.  
  
     È possibile caricare simboli o specificare un percorso simboli dalla finestra **Moduli** usando il menu di scelta rapida.  
  
## Caricamento dei simboli  
 Nella finestra **Moduli** vengono visualizzati i moduli con i simboli di debug caricati.  Queste informazioni sono visualizzate nella colonna **Stato simboli**.  Se lo stato è **Caricamento ignorato**, **Impossibile trovare o aprire il file PDB** o **Caricamento disabilitato dall'impostazione Include\/Exclude** è possibile usare il debugger per scaricare i simboli dai server dei simboli pubblici Microsoft oppure per caricare i simboli da una directory di simboli nel computer in uso.  Per altre informazioni, vedere [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
#### Per caricare i simboli manualmente  
  
1.  Nella finestra **Moduli** fare clic con il pulsante destro del mouse su un modulo per il quale non sono stati caricati i simboli.  
  
2.  Scegliere **Carica simboli da**, quindi fare clic su **Server dei simboli Microsoft** o **Percorso simboli**.  
  
#### Per modificare le impostazioni di caricamento dei simboli  
  
1.  Nella finestra **Moduli**, fare clic con il pulsante destro del mouse su un modulo.  
  
2.  Fare clic su **Impostazioni simboli**.  
  
     È ora possibile modificare le impostazioni di caricamento dei simboli, come descritto in [Specificare i percorsi dei simboli e il comportamento di caricamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).  Riavviare la sessione di debug per rendere effettive le modifiche.  
  
#### Per modificare il comportamento di caricamento dei simboli per un modulo specifico  
  
1.  Fare clic con il pulsante destro del mouse sul modulo nella finestra **Moduli**.  
  
2.  Scegliere **Impostazioni caricamento automatico simboli**, quindi fare clic su **Carica sempre manualmente** o **Predefinita**.  Riavviare la sessione di debug per rendere effettive le modifiche.  
  
## Vedere anche  
 [Breaking Execution](http://msdn.microsoft.com/it-it/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)