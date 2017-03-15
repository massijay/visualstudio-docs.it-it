---
title: "Supporta pi&#249; viste di documento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], personalizzato - più visualizzazioni di documento"
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Supporta pi&#249; viste di documento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile immettere più di una visualizzazione di un documento creando i dati dell'atto separato e gli oggetti visualizzazione del documento per l'editor.  Alcuni casi in cui una visualizzazione aggiuntiva del documento è opportuno sono:  
  
-   Supporto della nuova finestra: Utilizzare l'editor per fornire due o più visualizzazioni dello stesso tipo, in modo che un utente che dispone già di una finestra aperta in l possibile aprire una nuova finestra selezionando il comando di **nuova finestra** dal menu di **finestra** .  
  
-   Form e codificare il supporto di visualizzazione: Utilizzare l'editor per fornire le visualizzazioni di tipi diversi.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], ad esempio, fornendo sia una visualizzazione form che una visualizzazione codice.  
  
 Per ulteriori informazioni, vedere la procedura di CreateEditorInstance nel file di EditorFactory.cs nel progetto dell'editor personalizzato creato dal modello del pacchetto di Visual Studio.  per ulteriori informazioni su questo progetto, vedere [Procedura dettagliata: Creazione di un Editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## sincronizzare le visualizzazioni  
 Quando si distribuiscono le visualizzazioni multiple, l'oggetto dati del documento è responsabile della conservazione di tutte le visualizzazioni sincronizzate con i dati.  È possibile utilizzare le interfacce di gestione degli eventi in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> per sincronizzare le visualizzazioni multiple con i dati.  
  
 Se non si utilizza l'oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> per sincronizzare le visualizzazioni multiple, sarà necessario implementare per contenere il sistema di eventi per gestire le modifiche apportate all'oggetto dati del documento.  È possibile utilizzare i livelli diversi di granularità per mantenere le visualizzazioni più aggiornate.  Con un'impostazione di granularità massima, man mano che si digita una visualizzazione altre visualizzazioni vengono aggiornate contemporaneamente.  Con granularità minima, altre visualizzazioni non vengono aggiornate fino a attivarle esso.  
  
## Determinando se i dati del documento sono già aperti  
 La tabella in esecuzione il documento \(RDT\) nella barra di \(IDE\) avanzamento delle guide dell'ambiente di sviluppo integrato \(IDE\) se i dati di un documento sono già aperti, come illustrato nel diagramma seguente.  
  
 ![Grafica DocDataView](../extensibility/media/docdataview.png "Docdataview")  
Visualizzazioni multiple  
  
 Per impostazione predefinita, ogni visualizzazione \(oggetto visualizzazione di documento\) è contenuta nella propria struttura della finestra \(<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>\).  Come già accennato, tuttavia, i dati del documento può essere visualizzato nelle visualizzazioni multiple.  Per abilitare questa opzione, verrà esaminato il RDT per determinare se il documento in questione sia già aperto in un editor.  When the IDE calls <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> to create the editor, a non\-NULL value returned in the `punkDocDataExisting` parameter indicates that the document is already open in another editor.  Per ulteriori informazioni sull'RDT viene eseguita, vedere [Tabella Document in esecuzione](../extensibility/internals/running-document-table.md).  
  
 Nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , esaminare l'oggetto dati del documento restituito in `punkDocDataExisting` per determinare se i dati del documento sono appropriati per l'editor.  Ad esempio, solo i dati HTML devono essere visualizzato da un editor HTML.\) Se il test è appropriato, la factory dell'editor deve fornire una seconda visualizzazione dei dati.  Se il parametro di `punkDocDataExisting` non è `NULL`, è possibile uno che l'oggetto dati del documento aperto in un altro editor, o, generalmente, i dati del documento sono già aperti in una visualizzazione diversa con lo stesso editor.  Se i dati del documento sono aperti in un editor diverso dalla factory dell'editor non supporta, Visual Studio non riesce a aprire la factory dell'editor.  Per ulteriori informazioni, vedere [Procedura: collegare visualizzazioni per tenere traccia dei dati](../extensibility/how-to-attach-views-to-document-data.md).