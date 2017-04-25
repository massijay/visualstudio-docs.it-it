---
title: Impostazioni progetto di VC++, Progetti e soluzioni, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: fbe834e4e8178a129f68cec1c4a78ffea3c9fd7c
ms.lasthandoff: 04/25/2017

---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Impostazioni progetto di VC++, Progetti e soluzioni, finestra di dialogo Opzioni
Questa finestra di dialogo consente di definire le impostazioni del progetto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] relative ai log di compilazione e ai tipi di file supportati.  
  
### <a name="to-access-this-dialog-box"></a>Per accedere a questa finestra di dialogo  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Selezionare **Progetti e soluzioni** e quindi **Impostazioni progetto di VC++**.  
  
## <a name="build-customization-search-path"></a>Percorso di ricerca per le personalizzazioni delle compilazioni  
 Specifica l'elenco delle directory che contengono i file con estensione rule, che consentono di definire le regole di compilazione per i progetti.  
  
## <a name="build-logging"></a>Log di compilazione  
 **Sì**  
 Attiva la generazione del file di log di compilazione. Con questa opzione viene generato il file BuildLog.htm, reperibile nella directory dei file intermedi del progetto. Tale file viene sovrascritto a ogni nuova ricompilazione.  
  
 **No**  
 Disattiva la generazione del file di log di compilazione.  
  
## <a name="build-timing"></a>Durata compilazione  
 **Sì**  
 Attiva la registrazione della durata della compilazione. Se questa opzione è selezionata, il tempo necessario per il completamento della compilazione viene inviato alla finestra di output. Per altre informazioni, vedere [Finestra di output](../../ide/reference/output-window.md).  
  
 **No**  
 Disattiva la registrazione della durata della compilazione.  
  
## <a name="extensions-to-hide"></a>Estensioni da nascondere  
 Specifica le estensioni di file che non verranno visualizzate in **Esplora soluzioni** quando l'opzione **Mostra tutti i file** è abilitata.  
  
## <a name="extensions-to-include"></a>Estensioni da includere  
 Specifica le estensioni di file che è possibile trasferire nel progetto.  
  
## <a name="maximum-concurrent-c-compilations"></a>Numero massimo di compilazioni C++ simultanee  
 Specifica il numero massimo di core CPU da usare per la compilazione C++ in parallelo.  
  
## <a name="show-environment-in-log"></a>Mostra ambiente nel log  
 **Sì**  
 Elenca le variabili di ambiente presenti nel file di log di compilazione. Questa opzione specifica se attivare o meno nel file di log di compilazione l'eco di tutte le variabili di ambiente durante la compilazione di progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 **No**  
 Esclude le variabili di ambiente dal file di log di compilazione.  
  
## <a name="solution-explorer-mode"></a>Modalità Esplora soluzioni  
 **Mostra solo i file del progetto**  
 Configura **Esplora soluzioni** in modo da visualizzare solo i file del progetto.  
  
 **Mostra tutti i file**  
 Configura **Esplora soluzioni** in modo da visualizzare i file del progetto e quelli presenti su disco nella cartella del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di programmi C/C++](/cpp/build/building-c-cpp-programs)   
 [Riferimenti alla compilazione in C/C++](/cpp/build/reference/c-cpp-building-reference)
