---
title: "Aggiunta di directory per la finestra di dialogo Nuovo progetto | Microsoft Docs"
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
  - "Finestra di dialogo Nuovo progetto, estensione"
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Aggiunta di directory per la finestra di dialogo Nuovo progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando si creano nuovi tipi di progetto, è anche possibile registrare una nuova directory nella finestra di dialogo di **nuovo progetto** per visualizzare per l'utilizzo come modelli.  Nell'esempio di codice seguente viene illustrato come registrare una nuova directory, noto anche come nodo.  Nell'esempio, i modelli esposti da un VSPackage CLSID\_Package registrati.  Di conseguenza, il lato sinistro della finestra di dialogo di **nuovo progetto** offre il nodo aggiunto, con un nome basato sulla risorsa di Folder\_Label\_ResID.  Questa risorsa caricata da DLL satellite di package VS.  
  
 Il valore di **cartella** rappresenta un GUID di una cartella in cui il nodo di Folder\_Label\_ResID visualizzare.  Nell'esempio, il GUID rappresenta la cartella di **altri progetti** nel riquadro di **tipi di progetto** della finestra di dialogo di **nuovo progetto** .  Se il valore di **altri progetti** è presente, l'etichetta viene posizionato al livello.  
  
 Il valore di TemplatesDir specifica il percorso completo della directory contenente i modelli di progetto.  Questi file possono trovarsi in qualsiasi file VSZ o file modelli tipici da usare.  
  
 Se si specifica TemplatesLocalizedSubDir, deve essere ID di risorsa di stringa che indica la sottodirectory di TemplatesDir che utilizza i modelli localizzati.  Poiché [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica la risorsa di tipo stringa da una DLL satellite se presente, ogni DLL satellite può contenere un nome diverso di sottodirectory. Il valore di SortPriority specifica una proprietà di ordinamento.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## Vedere anche  
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Aggiunta di directory per il dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)