---
title: "Modello di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "automazione [Visual Studio SDK], implementazione di oggetti di progetto"
  - "modelli di progetto, automazione"
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Modello di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il passaggio successivo nel fornire automazione per il progetto è di distribuire gli oggetti del progetto standard: le raccolte di `ProjectItems` e di <xref:EnvDTE.Projects> ; gli oggetti di <xref:EnvDTE.ProjectItem> e di `Project` ; e gli oggetti rimanenti univoci all'implementazione.  questi oggetti standard sono definiti in file di Dteinternal.h.  Un'implementazione degli oggetti standard è fornita nell'esempio di BscPrj.  È possibile utilizzare queste classi come modelli per creare per degli oggetti del progetto standard che sono affiancati con gli oggetti del progetto da altri tipi di progetto.  
  
 Un utente di automazione presupporre poter chiamare <xref:EnvDTE.Solution>\("`<UniqueProjName>")`e <xref:EnvDTE.ProjectItems> \(`n`\) in cui n è un numero di indice per ottenere un progetto specifico nella soluzione.  La creazione di questa chiamata di automazione dell'ambiente a chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> nella gerarchia appropriata di progetto, passando VSITEMID\_ROOT come parametro di ID voce e VSHPROPID\_ExtObject come parametro di VSHPROPID.  `IVsHierarchy::GetProperty` restituisce un puntatore di `IDispatch` all'oggetto ActiveX che fornisce l'interfaccia principale di `Project` , implementato.  
  
 Di seguito viene riportata la sintassi di `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 I progetti per l'annidamento e le raccolte di utilizzo per creare gruppi di elementi di progetto.  Gli aspetti della gerarchia è simile al seguente.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 L'annidamento significa che un oggetto di <xref:EnvDTE.ProjectItem> può essere raccolta di <xref:EnvDTE.ProjectItems> contemporaneamente perché una raccolta di `ProjectItems` può contenere oggetti annidati.  Nell'esempio di base di progetto non viene dimostrato questo annidamento.  Implementa l'oggetto di `Project` , partecipate alla struttura del tipo di struttura ad albero che caratterizza la progettazione del modello di automazione generale.  
  
 L'automazione di progetto segue il percorso nel diagramma seguente.  
  
 ![Oggetti di progetto Visual Studio](~/extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automazione del progetto  
  
 Se non si distribuisce un oggetto di `Project` , l'ambiente restituirà ancora un oggetto generico di `Project` che contiene solo il nome del progetto.  
  
## Vedere anche  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>