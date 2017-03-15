---
title: "Apertura e salvataggio di elementi di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti di persistenza file [Visual Studio SDK]"
  - "file [Visual Studio], apertura e salvataggio"
  - "editor [Visual Studio SDK], file di persistenza"
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Apertura e salvataggio di elementi di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando si aggiunge un nuovo tipo di progetto, è necessario gestire l'apertura e il salvataggio dei file di progetti nell'ambiente di sviluppo integrato di \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Negli argomenti seguenti vengono descritti gli approcci diversi per i file di apertura e di salvataggio.  
  
## In questa sezione  
 [Visualizzazione di file utilizzando il comando Apri File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Viene fornita una spiegazione dettagliata di come l'ide gestisce il comando di **file aperto** e il ruolo dei progetti in risposta a questo comando.  
  
 [Visualizzazione di file utilizzando l'aperto con il comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Viene fornita una spiegazione dettagliata e dettagliate su come l'ide gestisce il comando di **Apri con** , richiedente apertura di un file con la scelta degli editor standard.  
  
 [Procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)  
 Vengono fornite istruzioni dettagliate per specificare che i file di un determinato tipo nel progetto vengano aperti utilizzando un editor specifico del progetto.  
  
 [Procedura: aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md)  
 Vengono fornite istruzioni dettagliate per specificare come consentire all'IDE per aprire un editor standard per i file del tipo di progetto.  
  
 [Procedura: aprire gli editor di documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Vengono fornite istruzioni dettagliate per aprire un editor specifico del progetto per un file aperto.  
  
 [Salvare un documento Standard](../../extensibility/internals/saving-a-standard-document.md)  
 Viene fornita una spiegazione dettagliata di come l'ide mantiene i controlli di **Salvare**, di **Salva con nome**e di **Salva tutto** per un documento aperto in un editor standard.  
  
 [Salvare un documento personalizzato](../../extensibility/internals/saving-a-custom-document.md)  
 Fornisce un diagramma e una spiegazione dettagliata di come l'ide mantiene i controlli di **Salvare**, di **Salva con nome**e di **Salva tutto** per i documenti aperti in un editor personalizzato.  
  
 [Determinazione di un File in un progetto che verrà aperto l'Editor](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Viene descritto il processo che l'ide segue per selezionare l'editor o la finestra di progettazione appropriato per un file.  
  
## Sezioni correlate  
 [Creazione di finestre di progettazione ed editor personalizzati](../../extensibility/creating-custom-editors-and-designers.md)  
 Elenca i quattro tipi di editor che l'ide può ospitare e fornisce descrizioni di ciascun editor.  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Viene illustrato come i progetti controllano il modo in cui il codice viene compilato e compilato, come gli editor vengono aperti e come elementi di progetto vengono formattati.