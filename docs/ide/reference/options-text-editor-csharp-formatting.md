---
title: "Opzioni, Editor di testo, C#, Formattazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting"
helpviewer_keywords: 
  - "formattazione [C#]"
  - "formattazione [J#]"
  - "Finestra di dialogo Opzioni dell'editor di testo, formattazione"
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 23
caps.handback.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opzioni, Editor di testo, C#, Formattazione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilizzare la pagina delle proprietà **Formattazione** della finestra di dialogo Opzioni per impostare le opzioni di formattazione del codice nell'Editor di codice.  Per accedere a questa finestra di dialogo, scegliere **Opzioni** dal menu **Strumenti**, espandere il nodo **Editor di testo**, quindi **C\#** e fare clic su **Formattazione**.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Impostazioni generali  
 Le impostazioni generali influiscono sul modo di applicare le opzioni di formattazione al codice nell'Editor di codice.  
  
## Elenco UIElement  
  
|Etichetta|Descrizione|  
|---------------|-----------------|  
|**Formatta automaticamente istruzione completata dopo l'immissione di ;**|Quando questa opzione è selezionata, vengono formattate le istruzioni al completamento in base alle opzioni di formattazione selezionate per l’editor di codice.  Deselezionare questa opzione se non si desidera modificare le istruzioni con l'Editor di codice.|  
|**Formatta automaticamente blocco completato dopo l'immissione di }**|Quando l'opzione è selezionata, i blocchi di codice vengono formattati in base alle opzioni di formattazione selezionate per l'Editor di codice subito dopo il completamento del blocco.  Deselezionare questa opzione se non si desidera modificare i blocchi con l'Editor di codice.|  
|**Modifica rientro dopo operazione Incolla**|Quando l'opzione è selezionata, il testo inserito nell'Editor di codice viene formattato in base alle opzioni di formattazione selezionate per l'Editor di codice.  Deselezionare questa opzione se non si desidera modificare il testo inserito.|  
  
## Finestra di anteprima  
 In ciascuno dei riquadri di opzioni **Rientro**, **Nuove righe**, **Spaziatura** e **Ritorno a capo** viene visualizzata una finestra di anteprima.  La finestra di anteprima consente di vedere l'effetto di ciascuna opzione.  Per utilizzare la finestra di anteprima, selezionare un'opzione di formattazione.  Nella finestra verrà mostrato un esempio dell'opzione selezionata.  Se si modifica questa impostazione, ad esempio si seleziona o deseleziona una casella di controllo, la finestra di anteprima viene aggiornata per visualizzare l’effetto della nuova impostazione.  
  
## Note  
 Le opzioni di rientro nelle pagine **Tabulazioni** per ogni linguaggio determinano solo il punto in cui l'editor del codice posiziona il cursore quando si preme INVIO alla fine di una riga.  Le opzioni di rientro in **Formattazione** si applicano quando il codice viene formattato automaticamente, ad esempio quando si inserisce codice nel file ed è selezionata l'opzione **Modifica rientro dopo operazione Incolla** o quando il blocco da formattare viene digitato manualmente.  
  
## Vedere anche  
 [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)