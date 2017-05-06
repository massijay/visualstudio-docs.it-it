---
title: "Elemento &lt;friendlyName&gt; (sviluppo per Office in Visual Studio)"
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
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <friendlyName>"
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Elemento &lt;friendlyName&gt; (sviluppo per Office in Visual Studio)
  L'elemento `friendlyName` dello spazio dei nomi `vstov4`  archivia il nome visualizzato nell'elenco dei programmi installati.  
  
## Sintassi  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## Elementi e attributi  
 L'elemento `friendlyName` si trova nello spazio dei nomi `vstov4` . Il valore viene visualizzato nell'elenco dei programmi installati nel computer e nella finestra di dialogo del componente aggiuntivo VSTO COM delle applicazioni Microsoft Office.  
  
 L'elemento `friendlyName` è privo di attributi o elementi figlio.  
  
## Esempio di componente aggiuntivo VSTO  
  
### Descrizione  
 L'esempio di codice seguente illustra l'elemento `friendlyName` in una soluzione a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  