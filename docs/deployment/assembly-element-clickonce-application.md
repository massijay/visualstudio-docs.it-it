---
title: "&lt;assembly&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "<assembly> element [ClickOnce application manifest]"
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# &lt;assembly&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Elemento di livello superiore del manifesto dell'applicazione.  
  
## Sintassi  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## Elementi e attributi  
 L'elemento `assembly` è l'elemento radice ed è obbligatorio.  Il primo elemento in esso contenuto deve essere un elemento `assemblyIdentity`.  Gli elementi del manifesto devono essere in uno dei seguenti spazi dei nomi:  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 Anche gli elementi figlio dell'assembly devono essere presenti in questi spazi dei nomi, per ereditarietà o per codifica.  
  
 L'elemento `assembly` presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`manifestVersion`|Obbligatorio.  L'attributo `manifestVersion` deve essere impostato su `1.0`.|  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un elemento `assembly` in un manifesto per un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  L'esempio di codice fa parte di un esempio più esaustivo fornito in [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<assembly\> Element](../deployment/assembly-element-clickonce-deployment.md)