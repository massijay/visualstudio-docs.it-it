---
title: "Introduzione al modello di progetto VSIX | Microsoft Docs"
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
  - "Visual Studio SDK, modello di progetto VSIX"
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Introduzione al modello di progetto VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare il modello di progetto VSIX per creare un'estensione o per un'estensione esistente per la distribuzione del pacchetto. Il modello di progetto VSIX con le versioni di Visual Basic e Visual c\# e viene installato come parte di Visual Studio SDK.  
  
 Il modello di progetto VSIX costituito solo da un file source.extension.vsixmanifest, che contiene informazioni sull'estensione e le risorse che è disponibile.  
  
 Per trovare il modello di progetto VSIX, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Distribuzione di un modello di progetto personalizzati utilizzando il modello di progetto VSIX  
 La procedura seguente viene illustrato come utilizzare il progetto VSIX per assemblare un modello di progetto che è possibile condividere con altri sviluppatori o caricare in Visual Studio Gallery.  
  
1.  Creare un modello di progetto.  
  
    1.  Aprire il progetto da cui creare un modello. Questo progetto può essere di qualsiasi tipo di progetto.  
  
    2.  Nel menu **File** scegliere**Esporta modello**. Completare i passaggi della procedura guidata.  
  
         Viene creato un file con estensione zip in %USERPROFILE%\\My Documents\\Visual Studio *\< versione \>*\\My Exported Templates\\.  
  
2.  Creare un progetto VSIX vuoto.  
  
     Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**. Selezionare l'opzione **Visual Basic** o **Visual c\#**. Selezionare il nodo selezionato, **estendibilità**, quindi selezionare **progetto VSIX**.  
  
3.  Aggiungere il file con estensione zip per il progetto. Impostare il relativo **Copia nella Directory di Output di** proprietà `Copy Always`.  
  
4.  Nel **Esplora**, fare doppio clic sul `source.extension.vsixmanifest` per aprirlo nel **Progettazione del manifesto VSIX**, e quindi apportare le modifiche seguenti:  
  
    -   Impostare il **nome prodotto** campo **risorse del modello di progetto**.  
  
    -   Impostare il **ID prodotto** campo **MyProjectTemplate \- 1**.  
  
    -   Impostare il **autore** campo **Fabrikam**.  
  
    -   Impostare il **Descrizione** campo **il modello di progetto**.  
  
    -   Nel **asset** sezione, aggiungere un **Microsoft.VisualStudio.ProjectTemplate** tipo e impostare il percorso per il nome del file ZIP.  
  
5.  Salvare e chiudere il file source.extension.vsixmanifest.  
  
6.  Compilare il progetto.  
  
7.  Nella directory di output, fare doppio clic sul file VSIX.  
  
8.  Oggetto **programma di installazione di VSIX** finestra di dialogo. Seguire le istruzioni per installare l'estensione.  
  
9. Chiudere Visual Studio e quindi aprirlo nuovamente.  
  
10. Selezionare **estensioni e aggiornamenti** \(nel **strumenti** menu\) e selezionare il **modelli** categoria. Deve essere una delle estensioni disponibili **risorse del modello di progetto**.  
  
11. Il nuovo modello di progetto visualizzato nel **Nuovo progetto** finestra di dialogo nella stessa posizione come il modello di progetto originale. Ad esempio, se è stato creato un modello denominato **Console VB** da un'applicazione console Visual Basic, **Console VB** viene visualizzata nello stesso riquadro come Visual Basic **applicazione Console** modello.  
  
#### Per specificare il percorso del modello nella finestra di dialogo Nuovo progetto  
  
1.  Cartelle dei modelli si trovano nel *percorso di installazione di Visual Studio*\\Common7\\IDE\\ProjectTemplates e *percorso di installazione di Visual Studio*\\Common7\\IDE\\ItemTemplates directory. I nomi delle sezioni di primo livello nella finestra di dialogo Nuovo progetto corrispondono esattamente i nomi delle cartelle dei modelli. Se sono diversi, utilizzare il nome della cartella del modello.  
  
     Modificare l'estensione di file con estensione VSIX in. zip e quindi aprire il file.  
  
2.  Creare una nuova cartella con lo stesso nome della sezione della finestra di dialogo Nuovo progetto in che modello risulterà.  
  
3.  Se il modello deve trovarsi in una sottosezione, creare una sottocartella con lo stesso nome.  
  
4.  Spostare il file zip del modello nella nuova cartella.  
  
5.  Modificare l'estensione. zip in VSIX.  
  
6.  Aprire il manifesto VSIX.  
  
7.  Nel manifesto VSIX, aggiornare il **Asset** percorso del modello in modo che punti alla radice della struttura di directory che contiene il file di modello. Ad esempio, se il modello è \\CSharp\\Windows, \\CSharp deve puntare il riferimento.