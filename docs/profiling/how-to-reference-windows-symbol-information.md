---
title: "Procedura: Fare riferimento alle informazioni sui simboli di Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per le prestazioni, server di simboli"
  - "server, server dei simboli"
  - "strumenti per la profilatura, server di simboli"
  - "server di simboli"
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Fare riferimento alle informazioni sui simboli di Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli strumenti di profilatura di Visual Studio utilizzano file di simboli \(con estensione pdb\) per risolvere i nomi simbolici, ad esempio i nomi delle funzioni nei file binari del programma.  È possibile seguire questa procedura per scaricare e aggiornare automaticamente i file pdb corretti per la versione di Windows presente sul computer locale.  
  
> [!NOTE]
>  Questa impostazione non influisce sui rapporti esistenti.  Infatti le informazioni sui simboli saranno presenti solo nei report creati dopo la specifica del server di simboli.  
  
 Per ulteriori informazioni, vedere [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### Utilizzare il server simboli Microsoft  
  
1.  Creare una cartella per contenere le informazioni sul file di simboli, ad esempio C:\\SymbolCache.  
  
2.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
     Verrà visualizzata la finestra di dialogo **Opzioni**.  
  
3.  Espandere la struttura ad albero **Debug** e fare clic su **Simboli**.  
  
4.  In **Percorsi dei file di simboli \(.pdb\)**, selezionare **Server dei simboli Microsoft**  
  
5.  Digitare il percorso della cartella creata nel passaggio 1 in **Memorizza nella cache i simboli dai server di simboli in questa directory**, ad esempio:  
  
     C:\\SymbolCache  
  
     È inoltre possibile fare clic sul pulsante con i puntini di sospensione \(**…**\) quindi selezionare una directory nella finestra di dialogo **Cerca cartella**.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Procedura: Serializzare le informazioni sui simboli](../profiling/how-to-serialize-symbol-information.md)