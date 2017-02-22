---
title: "Impostazioni progetto di VC++, Progetti e soluzioni, finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VCBuild"
helpviewer_keywords: 
  - "compilazioni [Visual Studio], log"
  - "processo di compilazione [C++]"
  - "file [Visual Studio], generati dal compilatore C/C++"
  - "estensioni di file, generati dal compilatore C o C++"
  - "cl.exe (compilatore), estensioni di file"
  - "estensioni, file generati dal compilatore C o C++"
  - "BuildLog.htm"
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Impostazioni progetto di VC++, Progetti e soluzioni, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo consente di definire le impostazioni del progetto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] relative al log di compilazione e ai tipi di file di supporto.  
  
### Per accedere a questa finestra di dialogo  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Selezionare **Progetti e soluzioni**, quindi scegliere **Impostazioni progetto di VC\+\+**.  
  
## Percorso di ricerca delle personalizzazioni di compilazione  
 Specifica l'elenco delle directory che contengono i file RULE, che aiutano a definire le regole di compilazione dei progetti.  
  
## Log di compilazione  
 **Sì**  
 Attiva la creazione del file di log di compilazione.  Questa opzione consente di generare il file BuildLog.htm, che è possibile reperire nella directory dei file intermedi del progetto.  A ogni ricompilazione il file BuildLog.htm precedente viene sovrascritto.  
  
 **No**  
 Disattiva la creazione del file di log di compilazione.  
  
## Temporizzazione del processo di compilazione  
 **Sì**  
 Attiva la temporizzazione del processo di compilazione.  Se l'opzione è selezionata, il tempo impiegato per il completamento della compilazione viene inviato alla finestra di output.  Per ulteriori informazioni, vedere [Finestra di output](../../ide/reference/output-window.md).  
  
 **No**  
 Disattiva la temporizzazione del processo di compilazione.  
  
## Estensioni da nascondere  
 Consente di specificare le estensioni dei file che non saranno visualizzati in **Esplora soluzioni** quando è abilitata l'opzione **Mostra tutti i file**.  
  
## Estensioni da includere  
 Consente di specificare le estensioni dei file che è possibile trasferire nel progetto.  
  
## Compilazioni in C\+\+ simultanee massime  
 Specifica il numero massimo di core della CPU da utilizzare per la compilazione in C\+\+ parallela.  
  
## Mostra ambiente nel log  
 **Sì**  
 Elenca le variabili di ambiente nel file di log di compilazione.  Questa opzione specifica se attivare o meno l'eco di tutte le variabili di ambiente durante la compilazione dei progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] nel file di log di compilazione.  
  
 **No**  
 Esclude le variabili di ambiente dal file di log di compilazione.  
  
## Modalità Esplora soluzioni  
 **Mostra solo file del progetto**  
 Consente di configurare **Esplora soluzioni** in modo da visualizzare solo i file del progetto.  
  
 **Mostra tutti i file**  
 Consente di configurare **Esplora soluzioni** in modo da visualizzare i file nel progetto e i file su disco nella cartella del progetto.  
  
## Vedere anche  
 [Compilazione di programmi C\/C\+\+](/visual-cpp/build/building-c-cpp-programs)   
 [Riferimenti alla compilazione in C\/C\+\+](/visual-cpp/build/reference/c-cpp-building-reference)