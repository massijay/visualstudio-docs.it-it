---
title: 'Procedura dettagliata: Personalizzazione della visualizzazione di testo | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e40368ed6aaf68b747f19cffe4e378a89ff6c0b5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-customizing-the-text-view"></a>Procedura dettagliata: Personalizzazione della visualizzazione di testo
È possibile personalizzare una visualizzazione testo modificando le proprietà seguenti nella mappa formato dell'editor:  
  
-   Margine indicatore  
  
-   Punto di inserimento  
  
-   Sovrascrivere l'accento circonflesso  
  
-   Testo selezionato  
  
-   Testo selezionato inattivo (vale a dire testo selezionato che ha perso lo stato attivo)  
  
-   Lo spazio vuoto  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo, selezionare **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `ViewPropertyTest`.  
  
2.  Aggiungere un modello di elemento Editor classificatore al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="defining-the-content-type"></a>Definizione del tipo di contenuto  
  
1.  Aggiungere un file di classe e denominarla `ViewPropertyModifier`.  
  
2.  Aggiungere il codice seguente `using` direttive:  
  
     [!code-cs[N.&1; VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs) ] 
     [!code-vb [VSSDKViewPropertyTest n.&1;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Dichiarare una classe denominata `TestViewCreationListener` che eredita da <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Esportare questa classe con i seguenti attributi:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>Per specificare il tipo di contenuto a cui si applica questo listener.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>Per specificare il ruolo di questo listener.</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>  
  
     [!code-cs[N.&2; VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest n.&2;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  Questa classe, importare <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>  
  
     [!code-cs[N.&3; VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs) ] 
     [!code-vb [VSSDKViewPropertyTest n.&3;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Modifica delle proprietà di visualizzazione  
  
1.  Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>metodo in modo da visualizzare le proprietà vengono modificate quando viene aperta la visualizzazione.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Per apportare la modifica, trovare il <xref:System.Windows.ResourceDictionary>che corrisponde all'aspetto della visualizzazione si desidera trovare.</xref:System.Windows.ResourceDictionary> Quindi modificare la proprietà appropriata nel dizionario risorse e impostare le proprietà. Batch le chiamate al <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>metodo chiamando il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>metodo prima di impostare le proprietà e quindi la <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>dopo aver impostato le proprietà.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>  
  
     [!code-cs[N.&4; VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs) ] 
     [!code-vb [VSSDKViewPropertyTest n.&4;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
  
1.  Compilare la soluzione.  
  
     Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
2.  Creare un file di testo e digitare alcune parole.  
  
    -   Il punto di inserimento deve essere magenta e il punto di inserimento di sovrascrittura deve essere turchese.  
  
    -   Il margine indicatore (a sinistra della visualizzazione di testo) deve essere luce verde.  
  
3.  Selezionare il testo che appena digitato. Il colore del testo selezionato deve essere chiaro rosa.  
  
4.  Mentre il testo è selezionato, fare clic all'esterno dell'intervallo di testo. Il colore del testo selezionato deve essere Rosa scuro.  
  
5.  Attivare lo spazio vuoto. (Nel **modificare** dal menu **avanzate** e quindi fare clic su **Mostra/Nascondi spazi**). Digitare alcune schede nel testo. Le frecce rosse indicano che rappresentano le schede devono essere visualizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio di linguaggio e punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md)
