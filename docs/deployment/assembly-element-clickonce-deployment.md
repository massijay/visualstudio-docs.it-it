---
title: "&lt;assembly&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assembly> element [ClickOnce deployment manifest]"
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;assembly&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Elemento di livello superiore del manifesto di distribuzione.  
  
## Sintassi  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## Elementi e attributi  
 L'elemento `assembly` è l'elemento radice ed è obbligatorio.  Il primo elemento in esso contenuto deve essere un elemento `assemblyIdentity`.  Gli elementi del manifesto devono essere inclusi nei seguenti spazi dei nomi: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2` e `http://www.w3.org/2000/09/xmldsig#`.  Anche gli elementi figlio dell'assembly devono essere presenti in questi spazi dei nomi, per ereditarietà o per codifica.  
  
 L'elemento `assembly` presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`manifestVersion`|Obbligatorio.  Questo attributo deve essere impostato su `1.0`.|  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un elemento `assembly` in un manifesto di distribuzione per un'applicazione distribuita mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  L'esempio di codice fa parte di un esempio più esaustivo fornito per l'argomento [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## Vedere anche  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly\> Element](../deployment/assembly-element-clickonce-application.md)