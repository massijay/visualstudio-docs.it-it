---
title: "Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.InternationalSettings"
  - "VS.ToolsOptionsPages.Environment.International_Settings"
  - "VS.Environment.International Settings"
  - "VS.ToolsOptionsPag.Environment.International_Settings"
helpviewer_keywords: 
  - "Impostazioni internazionali (finestra di dialogo)"
  - "lingue, impostazioni ambiente"
  - "Finestra di dialogo Opzioni, impostazioni internazionali"
  - "lingue, specifica impostazione predefinita"
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La pagina Impostazioni internazionali consente di modificare la lingua predefinita quando ci sono più versioni in lingue diverse dell'IDE \(Integrated Development Environment\) installato sul proprio computer.  È possibile accedere a questa finestra di dialogo selezionando **Opzioni** dal menu **Strumenti** e scegliendo **Impostazioni internazionali** dalla cartella **Ambiente**.  Se questa pagina non viene visualizzata nell'elenco, selezionare **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.  
  
> [!NOTE]
>  Le opzioni disponibili nelle finestre di dialogo e i nomi e i percorsi dei comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida a seconda dell'edizione o delle impostazioni attive.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per altre informazioni vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Lingua**:  
 Elenca le lingue disponibili per le versioni di lingua del prodotto installato.  Questa opzione non è disponibile a meno che non vi siano più versioni di lingua installate sul proprio computer.  Se l'ambiente è condiviso da più lingue di prodotti o da un'installazione mista di lingue dei prodotti, la selezione della lingua viene modificata in **Come Microsoft Windows**.  
  
> [!CAUTION]
>  In un sistema con più lingue installate, gli strumenti di compilazione Visual C\+\+ \(cl.exe, link.exe, nmake.exe, bscmake.exe e file correlati\) non sono interessati da questa impostazione.  Questi strumenti usano la versione dell'ultima lingua installata, sovrascrivendo quelli per la lingua precedentemente installata perché gli strumenti di compilazione di Visual C\+\+ non usano il modello DLL satellite.  
  
## Vedere anche  
 [Installazione di più versioni in lingue diverse di Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)