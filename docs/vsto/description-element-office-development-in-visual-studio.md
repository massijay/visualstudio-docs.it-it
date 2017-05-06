---
title: "Elemento &lt;description&gt; (sviluppo per Office in Visual Studio)"
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
  - "description (elemento)"
  - "elemento <description>"
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <description>"
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Elemento &lt;description&gt; (sviluppo per Office in Visual Studio)
  L'elemento `description` dello spazio dei nomi `vstov4`  archivia la descrizione della soluzione Office che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.  
  
## Sintassi  
  
```  
<description>  
</description>  
```  
  
## Elementi e attributi  
 Facoltativo. L'elemento `description` si trova nello spazio dei nomi `vstov4` . Contiene la descrizione del componente aggiuntivo che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.  
  
 L'elemento `description` è privo di attributi o elementi.  
  
## Esempio di componente aggiuntivo VSTO  
  
### Descrizione  
 L'esempio di codice seguente illustra l'elemento `description` in una soluzione a livello di applicazione distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstov4:description> ContosoOutlookAddIn - Outlook add-in created with Visual Studio Tools for Office </vstov4:description>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  