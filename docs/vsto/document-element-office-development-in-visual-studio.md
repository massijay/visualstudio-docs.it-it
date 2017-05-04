---
title: "Elemento &lt;document&gt; (sviluppo per Office in Visual Studio) | Microsoft Docs"
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
  - "document (elemento)"
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <document>"
  - "<document> (elemento)"
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Elemento &lt;document&gt; (sviluppo per Office in Visual Studio)
  L'elemento `document` dello spazio dei nomi `vstov4` contiene informazioni specifiche delle personalizzazioni a livello di documento.  
  
## Sintassi  
  
```  
<document solutionId />  
```  
  
## Elementi e attributi  
 Obbligatorio solo per personalizzazioni a livello di documento.  L'elemento `document` è nello spazio dei nomi `vstov4` .  L'elemento `document` dispone dei seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`solutionId`|Obbligatorio.  Il GUID utilizzato dal runtime di Visual Studio Tools per Office per identificare in modo univoco di una soluzione a livello di documento.  Il valore è archiviato come la proprietà del documento personalizzata \_AssemblyLocation.  Per ulteriori informazioni, vedere [Cenni preliminari sulle proprietà personalizzate dei documenti](../vsto/custom-document-properties-overview.md).|  
  
 `document` non contiene alcun elemento figlio.  
  
## Esempio di personalizzazione a livello di documento  
  
### Descrizione  
 Nell'esempio di codice seguente viene illustrato l'elemento `document` in una soluzione Office a livello di documento distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  Questo esempio di codice fa parte di un esempio più esaustivo fornito in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  