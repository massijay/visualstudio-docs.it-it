---
title: "Creazione di un&#39;estensione con un modello di elemento di Editor | Microsoft Docs"
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
  - "editor [Visual Studio SDK], nuovo - estensioni"
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione di un&#39;estensione con un modello di elemento di Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare modelli di elementi inclusi nel SDK di Visual Studio per creare estensioni dell'editor di base che aggiungono classificatori, grafici e i margini nell'editor. I modelli di elemento editor sono disponibili per i progetti Visual c\# o Visual Basic VSIX.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un'estensione di classificazione  
 Il modello di elemento classificatore Editor Crea un classificatore editor che il testo appropriato i colori \(in questo caso, tutti gli elementi\) in qualsiasi file di testo.  
  
1.  Nel **Nuovo progetto** finestra di dialogo espandere **Visual c\#** o **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** selezionare **progetto VSIX**. Nel **nome** digitare `TestClassifier`. Fare clic su **OK**.  
  
2.  Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Passare a Visual c\# **estendibilità** nodo e selezionare **classificatore Editor**. Lasciare il nome file predefinito \(EditorClassifier1.cs\).  
  
3.  Esistono tre file di codice, come indicato di seguito:  
  
    -   EditorClassifier1.cs contiene la `EditorClassifier1` classe.  
  
    -   EditorClassifier1ClassificationDefinition.cs contiene la `OEditorClassifier1ClassificationDefinition` classe.  
  
    -   EditorClassifier1Format.cs contiene la `EditorClassifier1Format`  classe.  
  
    -   EditorClassifier1Provider.cs contiene la `EditorClassifier1Provider` classe.  
  
4.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale di Visual Studio.  
  
     Se si apre un file di testo, tutto il testo è sottolineato su uno sfondo violetto.  
  
## Creazione di un'estensione dell'area di controllo relativo al testo  
 Il modello di area di controllo Text Editor crea un'area di controllo relativo al testo che decora tutte le istanze dei caratteri di testo 'a' utilizzando una casella con un contorno rosso e uno sfondo blu. È relativo al testo perché la casella sempre sovrapposte 'a' caratteri, anche quando vengono spostati o riformattati.  
  
1.  Nel **Nuovo progetto** finestra di dialogo espandere **Visual c\#** o **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** selezionare **progetto VSIX**. Nel **nome** digitare `TestAdornment`. Fare clic su **OK**.  
  
2.  Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Passare a Visual c\# **estendibilità** nodo e selezionare **Editor di testo Adornment**. Lasciare il nome file predefinito \(TextAdornment1.cs\/vb\).  
  
3.  Esistono due file di codice, come indicato di seguito:  
  
    -   TextAdornment1.cs contiene la `TextAdornment1` classe.  
  
    -   extAdornment1TextViewCreationListener.cs contiene la `TextAdornment1TextViewCreationListener` classe.  
  
4.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale. Se si apre un file di testo, tutti i 'a' caratteri nel testo vengono evidenziati in rosso su uno sfondo blu.  
  
## Creazione di un'estensione dell'area di controllo relativo al riquadro di visualizzazione  
 Il modello di Editor Viewport Adornment crea un adornment relativo al riquadro di visualizzazione che consente di aggiungere una casella viola con un contorno rosso nell'angolo superiore destro del riquadro di visualizzazione.  
  
> [!NOTE]
>  Il *viewport* è l'area di visualizzazione di testo che è attualmente visualizzata.  
  
#### Per creare un'estensione dell'area di controllo del riquadro di visualizzazione utilizzando il modello di area di controllo del riquadro di visualizzazione dell'Editor  
  
1.  Nel **Nuovo progetto** finestra di dialogo espandere **Visual c\#** o **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** selezionare **progetto VSIX**. Nel **nome** digitare `ViewportAdornment`. Fare clic su **OK**.  
  
2.  Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Passare a Visual c\# **estendibilità** nodo e selezionare **Editor Viewport Adornment**. Lasciare il nome file predefinito \(ViewportAdornment1.cs\/vb\).  
  
3.  Esistono due file di codice, come indicato di seguito:  
  
    -   ViewportAdornment1.cs contiene la `ViewportAdornment1` classe.  
  
    -   ViewportAdornment1TextViewCreationListener.cs contiene il `ViewportAdornment1TextViewCreationListener` \(classe\)  
  
4.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale. Se si crea un nuovo file di testo, una casella viola con un contorno rosso viene visualizzata nell'angolo superiore destro del riquadro di visualizzazione.  
  
## Creazione di un'estensione di margine  
 Il modello di margine dell'Editor Crea un margine verde che viene visualizzato con le parole "Hello world\!" sotto la barra di scorrimento orizzontale.  
  
#### Per creare un'estensione di margine utilizzando il modello di margine dell'Editor  
  
1.  Nel **Nuovo progetto** finestra di dialogo espandere **Visual c\#** o **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** selezionare **progetto VSIX**. Nel **nome** digitare `MarginExtension`. Fare clic su **OK**.  
  
2.  Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Passare a Visual c\# **estendibilità** nodo e selezionare **Editor Viewport Adornment**. Lasciare il nome file predefinito \(EditorMargin1.cs\/vb\).  
  
3.  Esistono due file di codice, come indicato di seguito:  
  
    -   EditorMargin1.cs contiene la `EditorMargin1` classe.  
  
    -   EditorMargin1Factory.cs contiene la `EditorMargin1Factory` classe.  
  
4.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale. Se si apre un file di testo, un margine verde con le parole "Hello EditorMargin1" viene visualizzato sotto la barra di scorrimento orizzontale.  
  
## Vedere anche  
 [Servizio di linguaggio e punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md)