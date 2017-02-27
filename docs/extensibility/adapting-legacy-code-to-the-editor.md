---
title: "Adattamento del codice Legacy nell&#39;editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - schede"
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Adattamento del codice Legacy nell&#39;editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor di Visual Studio comprende molte funzionalità che è possibile accedere da componenti di codice esistenti. Nelle istruzioni seguenti viene illustrato come adattare il componente non MEF, ad esempio, un VSPackage, utilizzare la funzionalità di editor. Nelle istruzioni viene illustrato inoltre come utilizzare gli adapter per ottenere i servizi dell'editor di codice gestito e gestito.  
  
## Schede editor  
 Schede editor o gli shim, sono wrapper per gli oggetti di editor che espongono anche le classi e le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop> API. È possibile utilizzare le schede per spostarsi tra i servizi non di editor, ad esempio, i comandi della shell di Visual Studio e servizi di editor. \(Si tratta come l'editor è attualmente ospitato in Visual Studio\). Schede inoltre abilitare legacy estensioni del servizio editor e della lingua di funzionare correttamente in Visual Studio.  
  
## Utilizzo di adattatori di Editor  
 Il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> fornisce metodi che passa tra le nuove interfacce di editor e le interfacce legacy, nonché metodi che creano le schede.  
  
 Se si utilizza questo servizio in un componente MEF, è possibile importare il servizio come indicato di seguito.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Se si desidera utilizzare questo servizio in un componente non MEF, seguire le istruzioni nella sezione "Utilizzando Visual Studio Editor servizi in un Non\-componente MEF" più avanti in questo argomento.  
  
## Passaggio tra la nuova API Editor e l'API Legacy  
 Utilizzare i metodi seguenti per passare da un oggetto editor e un'interfaccia legacy.  
  
|Metodo|Conversione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Converte un <xref:Microsoft.VisualStudio.Text.ITextBuffer> a un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Converte un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> a un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Converte un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> a un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Converte un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> a un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Converte un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## Creazione di adattatori  
 Utilizzare i metodi seguenti per creare adattatori per le interfacce legacy.  
  
|Metodo|Conversione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> specificato <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crea un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## Creazione di adattatori nel codice non gestito  
 Tutte le classi di adapter registrate per essere locale condiviso generabile e può essere creata un'istanza utilizzando il `VsLocalCreateInstance()` \(funzione\).  
  
 Tutte le schede vengono create utilizzando il GUID che sono definiti nel file vsshlids.h il... Cartella \\VisualStudioIntegration\\Common\\Inc\\ dell'installazione di Visual Studio SDK. Per creare un'istanza di VsTextBufferAdapter, utilizzare il codice seguente.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## Creazione di adattatori nel codice gestito  
 Nel codice gestito, è possibile creare le schede condiviso nello stesso modo di quello descritto per codice non gestito. È inoltre possibile utilizzare un servizio MEF che consente di creare e interagire con gli adapter. In questo modo di ottenere un adattatore consente un controllo più accurato rispetto a quanto disponibile durante la creazione condivisa.  
  
#### Per creare un adattatore per IVsTextView  
  
1.  Aggiungere un riferimento a Microsoft.VisualStudio.Editor.dll. Assicurarsi che `CopyLocal` è impostato su `false`.  
  
2.  Creare un'istanza di <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, come indicato di seguito.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Chiamare il metodo `CreateX()`.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## Utilizzando l'Editor di Visual Studio direttamente dal codice non gestito  
 Lo spazio dei nomi Microsoft.VisualStudio.Platform.VSEditor e lo spazio dei nomi Microsoft.VisualStudio.Platform.VSEditor.Interop espongono interfacce COM callable come interfacce IVx \*. Ad esempio, l'interfaccia Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer è la versione COM di <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfaccia. Dal `IVxTextBuffer`, è possibile ottenere l'accesso per gli snapshot del buffer, modificare il buffer, ascolto degli eventi di modifica di testo nel buffer e creare punti di rilevamento e intervalli. I passaggi seguenti mostrano come accedere a un `IVxTextBuffer` da un `IVsTextBuffer`.  
  
#### Per ottenere un oggetto IVxTextBuffer  
  
1.  Le definizioni per le interfacce IVx \* sono nel file VSEditor.h il... Cartella \\VisualStudioIntegration\\Common\\Inc\\ dell'installazione di Visual Studio SDK.  
  
2.  Il codice seguente crea un'istanza di un buffer di testo usando il `IVsUserData->GetData()` metodo. Nel codice seguente, `pData` è un puntatore a un `IVsUserData` oggetto.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## Utilizzo di servizi di Editor di Visual Studio in un componente Non MEF  
 Se si dispone di un componente di codice gestito esistente che non utilizza il framework MEF e si desidera utilizzare i servizi dell'editor di Visual Studio, è necessario aggiungere un riferimento all'assembly che contiene il ComponentModelHost VSPackage e il relativo servizio SComponentModel.  
  
#### Per utilizzare i componenti dell'editor di Visual Studio da un componente non MEF  
  
1.  Aggiungere un riferimento all'assembly Microsoft.VisualStudio.ComponentModelHost.dll di... Cartella \\common7\\ide\\. dell'installazione di Visual Studio. Assicurarsi che `CopyLocal` è impostato su `false`.  
  
2.  Aggiungere una privata `IComponentModel` membro alla classe in cui si desidera utilizzare i servizi di editor di Visual Studio, come indicato di seguito.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Creare un'istanza di modello del componente nel metodo di inizializzazione per il componente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Dopo questa operazione, è possibile ottenere uno dei servizi di editor di Visual Studio mediante la chiamata di `IComponentModel.GetService<T>()` metodo per il servizio desiderato.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```