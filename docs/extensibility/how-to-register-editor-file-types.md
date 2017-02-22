---
title: "Procedura: registrare i tipi di File dell&#39;Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - registrare tipi di file"
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: registrare i tipi di File dell&#39;Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il modo più semplice per registrare i tipi di file dell'editor è possibile utilizzare gli attributi di registrazione forniti come parte delle classi del framework \(MPF\) del pacchetto gestite [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] .  Se si distribuisce il pacchetto in codice nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], è anche possibile scrivere uno script del Registro di sistema che registra l'editor e le estensioni associate.  
  
## Registrazione mediante le classi di MPF  
  
#### Per registrare i tipi di file dell'editor utilizzando le classi di MPF  
  
1.  Fornire la classe di <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> con i parametri appropriati per l'editor nella classe del package VS.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     dove “. L'esempio„ rappresenta l'estensione registrata per questo editor e “32 " è il livello di priorità.  
  
     `projectGuid` è il GUID per i vari tipi di file, definito in <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>.  I vari tipi di file viene fornito, in modo che il file risultante non passa essere parte del processo di compilazione.  
  
     `TemplateDir` rappresenta la cartella contenente i file modelli inclusi nell'esempio di base gestito dell'editor.  
  
     `NameResourceID` definito nel file di Resources.h del progetto BasicEditorUI e identifica l'editor come “mia editor„.  
  
2.  Eseguire l'override del metodo <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Nell'implementazione del metodo di <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> , chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> e passare l'istanza della factory dell'editor viene utilizzato.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Questo passaggio vengono registrate sia la factory dell'editor delle estensioni di file dell'editor.  
  
3.  Annullare la registrazione delle factory dell'editor.  
  
     Le factory dell'editor vengono automaticamente si annulla la registrazione quando il package VS viene eliminato.  Se l'oggetto della factory dell'editor implementa l'interfaccia di <xref:System.IDisposable> , il relativo metodo di `Dispose` viene chiamato dopo che la factory dell'annullamento della registrazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Registrazione mediante uno script del Registro Di Sistema  
 Registrare la factory e i tipi di file dell'editor in codice nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] viene eseguito mediante uno script del Registro di sistema per scrivere le finestre il Registro di sistema, come illustrato nel seguente.  
  
#### Per registrare i tipi di file dell'editor utilizzando uno script del Registro di sistema  
  
1.  In lo script del Registro di sistema, definire la factory dell'editor e la stringa della factory GUID dell'editor come illustrato nella sezione di `GUID_BscEditorFactory` di script seguente del Registro di sistema.  Inoltre, definire l'estensione e la priorità di estensione di editor:  
  
    ```  
  
                NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions             {                 val rtf = d 50             }  
        }  
    }  
    ```  
  
     L'estensione di file dell'editor in questo esempio viene interpretata come “rich„ e la priorità è “50 ".  Le stringhe GUID sono definite in file Resource.h del progetto di esempio di BscEdit.  
  
2.  Registrare il package VS.  
  
3.  Registrare la factory dell'editor.  
  
     La factory dell'editor viene registrata nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> .  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     Le stringhe GUID sono definite in file Resource.h del progetto BscEdit.