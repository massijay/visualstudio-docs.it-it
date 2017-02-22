---
title: "Esposizione di oggetti di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "oggetti di progetto, che espongono"
  - "estendibilità, oggetti di progetto"
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Esposizione di oggetti di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Tipi di progetto personalizzato possono fornire gli oggetti di automazione per consentire l'accesso al progetto utilizzando interfacce di automazione. Ogni tipo di progetto deve fornire lo standard <xref:EnvDTE.Project> oggetto di automazione che è accessibile dalla <xref:EnvDTE.Solution>, che contiene una raccolta di tutti i progetti aperti nell'IDE. Ogni elemento del progetto deve essere esposto da un <xref:EnvDTE.ProjectItem> si accede con <xref:Project.ProjectItems>. Oltre a questi oggetti di automazione standard, progetti è possono scegliere di oggetti di automazione specifico.  
  
 È possibile creare oggetti di automazione personalizzata a livello di radice che è possibile accedere ad associazione tardiva dall'oggetto DTE radice tramite `DTE.<customeObjectName>` o `DTE.GetObject(“<customObjectName>”)`. Ad esempio, Visual C\+\+ Crea raccolta di progetti specifici del progetto di C\+\+ denominato "VCProjects" che è possibile accedere utilizzando DTE. VCProjects o DTE. GetObject\("VCProjects"\). È inoltre possibile creare un Project. Object, che è univoco per il tipo di progetto, un CodeModel, che è possibile eseguire query per il relativo oggetto più derivato, un elemento, che espone un FileCodeModel e ProjectItem. Object.  
  
 È una convenzione comune per i progetti per esporre un insieme di progetti personalizzati, specifici del progetto. Ad esempio, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Crea una raccolta di progetti specifici di C\+\+ che è quindi possibile accedere tramite `DTE.VCProjects` o `DTE.GetObject("VCProjects")`. È inoltre possibile creare un `Project.Object`, che è univoco per il tipo di progetto, un `Project.CodeModel`, che è possibile eseguire query per un oggetto più derivato, un `ProjectItem`, che espone `ProjectItem.Object`, e un `ProjectItem.FileCodeModel`.  
  
### Per contribuire a un oggetto VSPackage specifico per un progetto  
  
1.  Aggiungere le chiavi appropriate per il file. pkgdef del pacchetto Visual Studio.  
  
     Ad esempio, ecco le impostazioni. pkgdef per il progetto in linguaggio C\+\+:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation] "VCProjects"="" [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents] "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementare il codice di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> \(metodo\), come nell'esempio seguente.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject( /* [in]  */ LPCOLESTR       pszPropName, /* [out] */ IDispatch **    ppIDispatch) { ExpectedPtrRet(pszPropName); ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (m_fZombie) return E_UNEXPECTED; if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0) { return GetAutomationProjects(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } return E_INVALIDARG; }   
    ```  
  
     Nel codice, `g_wszAutomationProjects` è il nome della raccolta di progetti. Il `GetAutomationProjects` metodo crea un oggetto che implementa il `Projects` interfaccia e restituisce un `IDispatch` puntatore all'oggetto chiamante, come illustrato nell'esempio di codice seguente.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch) { ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (!m_srpAutomationProjects) { HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects); IfFailRet(hr); ExpectedExprRet(m_srpAutomationProjects != NULL); } return m_srpAutomationProjects.CopyTo(ppIDispatch); }  
    ```  
  
     È necessario scegliere un nome univoco per l'oggetto di automazione. Conflitti di nomi sono imprevedibili e conflitti di causano un nome di oggetto in conflitto per arbitrariamente generato se più tipi di progetto utilizzano lo stesso nome. È necessario includere alcuni aspetti del relativo nome di prodotto il nome dell'oggetto di automazione univoco o nome della propria società.  
  
     Personalizzata `Projects` oggetto collection è un punto di ingresso comodità per la parte rimanente del modello di automazione del progetto. L'oggetto di progetto è inoltre accessibile dal <xref:EnvDTE.Solution> raccolta di progetti. Dopo aver creato il codice e del Registro di sistema le voci appropriate che forniscono consumer `Projects` raccolta di oggetti, l'implementazione deve fornire rimanenti oggetti standard per il modello di progetto. Per altre informazioni, vedere [Modello di progetto](../../extensibility/internals/project-modeling.md).  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>