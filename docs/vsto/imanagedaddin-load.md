---
title: "IManagedAddin::Load"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "IManagedAddin::Load"
  - "metodo Load"
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# IManagedAddin::Load
  Chiamato quando viene caricato un componente aggiuntivo VSTO gestito.  
  
## Sintassi  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*bstrManifestURL*|Percorso completo del manifesto per il componente aggiuntivo VSTO.|  
|*pdispApplication*|Puntatore a un oggetto IDispatch che rappresenta l'applicazione host che sta caricando il componente aggiuntivo VSTO.|  
  
## Valore restituito  
 Valore HRESULT che indica se il metodo è stato completato correttamente.  
  
## Note  
 Un manifesto è un file \(in genere, un file XML\) che fornisce informazioni usate per consentire il caricamento del componente aggiuntivo VSTO. Un manifesto, ad esempio, può specificare il percorso dell'assembly del componente aggiuntivo VSTO e la classe del punto di ingresso per creare un'istanza quando viene caricato il componente aggiuntivo VSTO.  
  
 Il parametro *bstrManifestURL* contiene il valore della voce `Manifest` sotto la chiave del Registro di sistema HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<nome applicazione\>*\\Addins\\*\<ID componente aggiuntivo\>* per il componente aggiuntivo VSTO. Per altre informazioni, vedere [Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md).  
  
 Implementare il metodo [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) per eseguire attività come ad esempio la configurazione del dominio dell'applicazione e dei criteri di sicurezza per il componente aggiuntivo VSTO che viene caricato.  
  
## Vedere anche  
 [Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  