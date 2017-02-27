---
title: "&lt;publisherIdentity&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "publisherIdentity Element [ClickOnce deployment manifest], introduction"
  - "required element for signed manifests [ClickOnce], publisherIdentity Element"
  - "publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes"
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;publisherIdentity&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene informazioni sull'editore che ha firmato questo manifesto della distribuzione.  
  
## Sintassi  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## Elementi e attributi  
 L'elemento `publisherIdentity` è obbligatorio per i manifesti firmati.  Nella tabella riportata di seguito sono indicati gli attributi supportati dall'elemento `publisherIdentity`.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio.  Descrive l'identità della parte che ha pubblicato questa applicazione.|  
|`issuerKeyHash`|Obbligatorio.  Contiene l'hash SHA\-1 della chiave pubblica dell'autorità di certificazione.|  
  
#### Parametri  
  
## Valore proprietà\/Valore restituito  
  
## Eccezioni  
  
## Note  
  
## Requisiti  
  
## Sottotitolo