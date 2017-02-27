---
title: "Singole e multi-scheda viste | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], personalizzato - singole e multi-scheda viste"
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Singole e multi-scheda viste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un editor possibile creare tipi diversi di visualizzazioni.  Si consideri ad esempio una finestra dell'editor di codice, un altro è una finestra di progettazione.  
  
 Una visualizzazione multi\-a schede è una visualizzazione che dispone di più schede.  Ad esempio, l'editor HTML dispone di due schede nella parte inferiore: **Progettazione** e **database di origine**, ogni una visualizzazione logica.  La visualizzazione progettazione consente di visualizzare una pagina Web di cui è stato eseguito il rendering, mentre l'altro viene visualizzato il markup HTML che include la pagina Web.  
  
## Accedere alle visualizzazioni di ambiente fisico  
 Oggetti visualizzazione fisici del documento host di visualizzazioni, ognuno dei quali rappresenta una visualizzazione di dati nel buffer, ad esempio il codice o un form.  Di conseguenza, ogni oggetto visualizzazione del documento ha una visualizzazione fisica \(identificata da un elemento noto come una stringa di visualizzazione fisica\) e in genere in un'unica visualizzazione logica.  
  
 In alcuni casi, tuttavia, una visualizzazione fisica può avere due o più visualizzazioni logiche.  Alcuni esempi sono un editor con una finestra divisa con le visualizzazioni affiancate, o una finestra di progettazione che presenta una visualizzazione GUI\/Progettazione e la visualizzazione di codice\-dietro \-\- form.  
  
 Per consentire all'editor per accedere a tutte le visualizzazioni disponibili di ambiente fisico, è necessario creare una stringa univoca di visualizzazione di ambiente fisico per ogni tipo di oggetto visualizzazione del documento che la factory dell'editor possibile creare.  Ad esempio, la factory dell'editor di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] possibile creare gli oggetti visualizzazione del documento per una finestra del codice e una finestra di progettazione.  
  
## Creare visualizzazioni Multi\-A Schede  
 Tramite un oggetto visualizzazione del documento deve essere associato a una visualizzazione fisica in una stringa univoca di visualizzazione di ambiente fisico, è possibile posizionare le schede all'interno della visualizzazione fisica per attivare la visualizzazione dei dati in diversi modi.  In questa configurazione multi\-a schede, tutte le schede sono associate alla stessa stringa di visualizzazione fisica, ma ogni scheda viene fornita una visualizzazione logica diversa GUID.  
  
 Per creare una visualizzazione multi\-a schede per un editor, implementare l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> quindi associare una visualizzazione logica diversa il GUID \(<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>\) con ogni scheda creato.  
  
 L'editor di Visual Studio HTML è un esempio di un editor con una visualizzazione di multi\-TAB.  È **Progettazione** le schede e di **database di origine** .  A tale scopo, una visualizzazione logica diversa è associata a ogni scheda, `LOGICALVIEWID_TextView` per la scheda di **Progettazione** e `LOGICALVIEWID_Code` per la scheda di **database di origine** .  
  
 Specificando la visualizzazione logica appropriata, un VSPackage possibile accedere alla visualizzazione corrispondente a uno scopo, come progettare un form, modificando il codice, o il debug del codice.  Tuttavia, una delle finestre deve essere identificata dalla stringa null e questa deve corrispondere alla visualizzazione logica principale \(`LOGVIEWID_Primary`\).  
  
 Nella tabella seguente sono elencati i valori di visualizzazione logici disponibili e il relativo utilizzo.  
  
|LOGVIEWID GUID|utilizzo consigliato|  
|--------------------|--------------------------|  
|`LOGVIEWID_Primary`|Impostazione predefinita\/visualizzazione primaria della factory dell'editor.<br /><br /> Tutte le factory dell'editor devono supportare questo valore.  Questa visualizzazione è necessario utilizzare la stringa null come la stringa di visualizzazione fisica.  Almeno una visualizzazione logica deve essere impostata su questo valore.|  
|`LOGVIEWID_Debugging`|visualizzazione di debug.  In genere, i mapping di `LOGVIEWID_Debugging` gli stessi visualizzazione come `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Visualizzazione avviata dal comando di **Visualizza codice** .|  
|`LOGVIEWID_Designer`|Visualizzazione avviata dal comando di **form di visualizzazione** .|  
|`LOGVIEWID_TextView`|Visualizzazione dell'editor di testo.  Si tratta della visualizzazione che restituisce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, da cui è possibile accedere a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Richiede all'utente di scegliere la visualizzazione da utilizzare.|  
|`LOGVIEWID_ProjectSpecificEditor`|Passato dalla finestra di dialogo di **Apri con** a<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> quando l'utente sceglie “\(editor di progetto predefinito\)„ la voce.|  
  
 Sebbene la visualizzazione logica GUID sia estendibile, è possibile utilizzare solo la visualizzazione logica GUID definita nel package VS.  
  
 Chiusura, Visual Studio mantiene il GUID della factory dell'editor e delle stringhe di visualizzazione fisiche associate alla finestra del documento in modo da poter essere utilizzato per riaprire le finestre del documento alla riapertura.  Solo le finestre aperte quando una soluzione viene chiusa vengono salvate in modo permanente nel file di soluzione \(.suo\).  I valori corrispondono ai valori di `VSFPROPID_pszPhysicalView` e di `VSFPROPID_guidEditorType` passati nel parametro di `propid` nel metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> .  
  
## Esempio  
 Questo frammento viene illustrato come oggetto di <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> viene utilizzato per accedere a una visualizzazione che implementa `IVsCodeWindow`.  In this case, the <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> service is used to call <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> and request `LOGVIEWID_TextView`, which obtains a pointer to a window frame.  Un puntatore all'oggetto di visualizzazione del documento viene ottenuto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> e specificando un valore di `VSFPROPID_DocView`.  Dall'oggetto del documento, `QueryInterface` viene chiamato per `IVsCodeWindow`.  L'aspettativa in questo caso è che un editor di testo viene restituito e pertanto oggetto visualizzazione del documento restituito nel metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> è una finestra del codice.  
  
```cpp#  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## Vedere anche  
 [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md)   
 [Procedura: collegare visualizzazioni per tenere traccia dei dati](../extensibility/how-to-attach-views-to-document-data.md)   
 [Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)