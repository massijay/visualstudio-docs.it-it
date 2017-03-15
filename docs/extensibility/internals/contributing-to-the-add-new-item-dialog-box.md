---
title: "Che contribuiscono a di dialogo Aggiungi nuovo elemento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aggiungi nuovo elemento della finestra di dialogo che contribuiscono a"
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Che contribuiscono a di dialogo Aggiungi nuovo elemento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un sottotipo di progetto può fornire una nuova directory completo degli elementi della finestra di dialogo di **Aggiungi nuovo elemento** registrando i modelli di **aggiungere l'elemento** nella sottochiave del Registro di sistema di `Projects` .  
  
## Registrare i template aggiungi nuovo elemento  
 In questa sezione si trova sotto **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Projects** nel Registro di sistema.  Le voci del Registro di sistema di seguito si presuppone un progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aggregato da un sottotipo ipotetico di progetto.  Le voci per il progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sono elencate in.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 La sottochiave di `AddItemTemplates\TemplateDirs` contiene le voci del Registro di sistema con il percorso della directory in cui gli elementi resi disponibili nella finestra di dialogo di **Aggiungi nuovo elemento** vengono posizionati.  
  
 L'ambiente carica automaticamente tutti i dati di `AddItemTemplates` nella sottochiave del Registro di sistema di `Projects` .  Ciò può includere dati per le implementazioni di progetto di base nonché i dati per i tipi di sottotipo di progetto specifico.  ogni sottotipo di progetto è identificato da un tipo di progetto `GUID`.  Il sottotipo di progetto è possibile specificare che un set di alternativa di modelli di `Add Item` deve essere utilizzato per un'istanza di progetto condita particolare supporta l'enumerazione di `VSHPROPID_ AddItemTemplatesGuid` da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> per restituire il valore GUID del sottotipo di progetto.  Se la proprietà di `VSHPROPID_AddItemTemplatesGuid` non è specificato, il GUID di progetto di base viene utilizzato.  
  
 È possibile filtrare gli elementi nella finestra di dialogo di **Aggiungi nuovo elemento** implementando l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> l'oggetto di aggregazione sottotipo di progetto.  Ad esempio, un sottotipo di progetto che implementa un progetto di database mediante l'aggregazione un progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , può filtrare gli elementi specifici di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dalla finestra di dialogo di **Aggiungi nuovo elemento** implementando il filtro e a sua volta, possibile aggiungere elementi specifici del progetto di database supportano `VSHPROPID_ AddItemTemplatesGuid` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  Per ulteriori informazioni sul filtro e sull'aggiunta alla finestra di dialogo di **Aggiungi nuovo elemento** , vedere [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID per gli oggetti che vengono in genere utilizzati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)