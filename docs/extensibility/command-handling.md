---
title: "Gestione dei comandi | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - comandi (gestione)"
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Gestione dei comandi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor è possibile definire nuovi comandi. I comandi sono in genere visualizzati in un menu, in una barra degli strumenti o in un menu di scelta rapida.  
  
 Per ulteriori informazioni sulla definizione dei comandi e menu, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un servizio di linguaggio è possibile controllare il menu di scelta rapida vengono visualizzati nell'editor, intercettando le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumerazione. In alternativa, è possibile controllare il menu di scelta rapida in base al marcatore. Per ulteriori informazioni vedere [comandi importanti per i filtri di servizio di linguaggio](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Aggiunta di comandi a menu di scelta rapida dell'Editor  
 Per aggiungere un comando di menu di scelta rapida, è innanzitutto necessario definire un set di comandi di menu che appartengono a un gruppo specifico. L'esempio seguente è tratto dal file vsct generato come parte della procedura dettagliata [procedura dettagliata: aggiunta di funzionalità in un Editor personalizzato](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \< guid menu = "guidCustomEditorCmdSet" id = "IDMX_RTF" priorità = "0x0000" type = "Contesto">  
  
 \< guid padre = "guidCustomEditorCmdSet" id = "0" />  
  
 \< stringhe>  
  
 \< ButtonText>Menu di scelta rapida CustomEditor \< / ButtonText>  
  
 \< CommandName>CustomEditorContextMenu \< / CommandName>  
  
 \< / stringhe>  
  
 \< / menu>  
  
 \< / i menu>  
  
 Il testo precedente aggiunge un comando di menu di contesto con il testo **menu di scelta rapida CustomEditor**. Il GUID di Menu è del set di comandi che viene creato con questo editor, che il tipo è "Context".  
  
 È inoltre possibile utilizzare comandi predefiniti che non devono essere definiti nel file vsct. Ad esempio, se si esamina il file EditorPane.cs generato dal modello del pacchetto di Visual Studio, invece che un set di comandi predefiniti, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definito da <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, vengono gestite nei gestori di comando, ad esempio il metodo onSelectAll.  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)