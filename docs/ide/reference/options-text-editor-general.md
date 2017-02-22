---
title: "Opzioni, Editor di testo, Generale | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.General"
  - "VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL.General"
  - "vs.toolsoptionspages.text_editor"
  - "VS.ToolsOptionsPages.Text_Editor.XML.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL80.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSS"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL7.General"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL.General"
  - "vs.toolsoptionspages.text_editor.visual_jsharp"
  - "VS.ToolsOptionsPages.Text_Editor.F#.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.F#"
  - "VS.ToolsOptionsPages.Text_Editor.PL/SQL.General"
  - "VS.ToolsOptionsPages.Text_Editor.C/C++.General"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text"
  - "VS.ToolsOptionsPages.Text_Editor.HTML"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.General"
  - "VS.ToolsOptionsPages.Text_Editor"
  - "VS.ToolsOptionsPages.Text_Editor.F#.General"
  - "VS.ToolsOptionsPages.Text_Editor.XOML.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL"
  - "vs.toolsoptionspages.text_editor.c/c++"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL90.General"
  - "VS.ToolsOptionsPages.Text_Editor.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp"
helpviewer_keywords: 
  - "Editor di testo (finestra di dialogo Opzioni)"
  - "Editor di codice"
  - "Editor di testo [Visual Studio]"
  - "editor, impostazioni globali"
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 29
caps.handback.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opzioni, Editor di testo, Generale
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo consente di modificare le impostazioni globali per l'editor di testo e di codice di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Per visualizzare questa finestra di dialogo, scegliere **Opzioni** dal menu **Strumenti**, espandere la cartella **Editor di testo**, quindi fare clic su **Generale**.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Impostazioni  
 Trascina la selezione  
 Quando questa opzione è selezionata, è possibile spostare il testo selezionandolo e trascinandolo con il mouse in un'altra posizione all'interno del documento o in qualsiasi altro documento aperto.  
  
 Evidenzia delimitatore automatico  
 Quando questa opzione è selezionata, i caratteri di delimitazione che separano i parametri o le coppie elemento\-valore, così come le parentesi graffe corrispondenti, vengono evidenziati.  
  
 Revisioni  
 Quando l'editor di codice selezionato, una riga gialla verticale nel margine di selezione contrassegnare il codice modificato da durante l'ultimo salvataggio del file.  Quando si salvano le modifiche, le righe verticali diventano verde.  
  
 Rileva automaticamente codifica UTF\-8 senza firma  
 Per impostazione predefinita, l'editor rileva la codifica cercando indicatori dell'ordine dei byte o tag del set di caratteri.  Se nel documento corrente non vengono trovati indicatori o tag di questo tipo, l'editor di codice tenterà di rilevare automaticamente la codifica UTF\-8 analizzando le sequenze di byte.  Per disabilitare il rilevamento automatico della codifica, deselezionare questa opzione.  
  
## Visualizzazione  
 Margine selezione  
 Quando questa opzione è selezionata, viene visualizzato un margine verticale lungo il bordo sinistro dell'area di testo dell'editor.  È possibile fare clic nel margine per selezionare un'intera riga di testo oppure fare clic e trascinare per selezionare righe di testo consecutive.  
  
|Margine selezione attivato|Margine selezione disattivato|  
|--------------------------------|-----------------------------------|  
|![Schermata HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.png "vxSelmaron")|![Schermata HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 Margine indicatore  
 Quando questa opzione è selezionata, viene visualizzato un margine verticale all'esterno del bordo sinistro dell'area di testo dell'editor.  Facendo clic in questo margine vengono visualizzate un'icona e una descrizione comandi relative al testo.  Nel margine indicatore, ad esempio, vengono visualizzati punti di interruzione o collegamenti dell'Elenco attività.  Le informazioni del margine indicatore non vengono stampate.  
  
 Barra di scorrimento verticale  
 Quando questa opzione è selezionata, viene visualizzata una barra di scorrimento verticale che consente di scorrere verso l'alto e verso il basso per visualizzare gli elementi al di fuori dell'area di visualizzazione dell'editor.  Se non sono disponibili barre di scorrimento verticali, per scorrere è possibile utilizzare i tasti PGSU e PGGIÙ e i tasti di direzione.  
  
 Barra di scorrimento orizzontale  
 Quando questa opzione è selezionata, viene visualizzata una barra di scorrimento orizzontale che consente di scorrere da un lato all'altro per visualizzare gli elementi al di fuori dell'area di visualizzazione dell'editor.  Se non sono disponibili barre di scorrimento orizzontali, per scorrere è possibile utilizzare i tasti di direzione.  
  
 La riga corrente di evidenziazione  
 Una volta selezionato, viene visualizzata una casella grigia che la riga di codice in cui il cursore si trova.  
  
## Vedere anche  
 [Opzioni, Editor di testo, Tutti i linguaggi](../../ide/reference/options-text-editor-all-languages.md)   
 [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Opzioni, Editor di testo, Estensione file](../../ide/reference/options-text-editor-file-extension.md)   
 [Identificazione e personalizzazione dei tasti di scelta rapida](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [Personalizzazione dell'editor](../../ide/customizing-the-editor.md)   
 [Utilizzo di IntelliSense](../../ide/using-intellisense.md)