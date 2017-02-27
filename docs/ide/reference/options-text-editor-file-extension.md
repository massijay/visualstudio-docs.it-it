---
title: "Opzioni, Editor di testo, Estensione file | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.toolsoptionspages.text_editor.file_extension"
helpviewer_keywords: 
  - "estensioni di file, associazione a editor"
  - "Strumento di modifica"
  - "Opzioni (finestra di dialogo)"
  - "Strumento di modifica, selezione"
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Opzioni, Editor di testo, Estensione file
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La finestra di dialogo Opzioni consente di specificare il modo in cui tutti i file con determinate estensioni verranno gestiti nell'ambiente di sviluppo integrato \(IDE\) di Visual Studio.  Per ciascuna estensione immessa, è possibile selezionare uno strumento di modifica,  scegliendo così la finestra di progettazione o l'editor dell'IDE in cui verranno aperti i documenti di un determinato tipo.  Per visualizzare queste opzioni, scegliere **Opzioni** dal menu **Strumenti**, espandere il nodo **Editor di testo** e selezionare **Estensione di file**.  
  
 Quando si seleziona un'opzione "con codifica", ogni volta che si apre un documento di tale tipo verrà visualizzata una finestra di dialogo che consente di selezionare uno schema di codifica per il documento.  Ciò può rivelarsi utile se si preparano versioni dei documenti di progetto da utilizzare su piattaforme diverse o con lingue di destinazione diverse.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Elenco UIElement  
 **Estensione**  
 Digitare l'estensione di file di cui si desidera definire lo strumento di modifica nell'IDE.  
  
 **Editor**  
 Selezionare la finestra di progettazione o l'editor dell'IDE in cui verranno aperti i documenti con l'estensione di file specificata.  Quando si seleziona un'opzione "con codifica", ogni volta che si apre un documento verrà visualizzata una finestra di dialogo che consente di selezionare uno schema di codifica.  
  
 **Aggiungi**  
 Consente di aggiungere una voce comprendente l'estensione e lo strumento di modifica specificati all'elenco delle estensioni.  
  
 **Rimuovi**  
 Consente di eliminare la voce selezionata dall'elenco delle estensioni.  
  
 Elenco estensioni  
 Contiene tutte le estensioni per cui è stato specificato uno strumento di modifica.  
  
 **Associa file senza estensione a**  
 Selezionare questa opzione se si desidera specificare come devono essere gestiti nell'IDE i file senza estensione.  
  
 **Opzioni per file senza estensione**  
 Viene fornito lo stesso elenco di **Editor**.  Selezionare la finestra di progettazione o l'editor dell'IDE in cui verranno aperti i documenti senza estensione di file.  
  
## Vedere anche  
 [Procedura: gestire le modalità dell'editor](../../ide/how-to-manage-editor-modes.md)