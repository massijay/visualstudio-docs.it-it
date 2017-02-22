---
title: "&lt;customErrorReporting&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "<customErrorReporting> element [ClickOnce deployment manifest]"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;customErrorReporting&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica un URI da visualizzare quando si verifica un errore.  
  
## Sintassi  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## Note  
 Questo elemento è facoltativo.  Se non viene utilizzato, in [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verrà visualizzata una finestra di dialogo di errore con lo stack dell'eccezione.  Se l'elemento `customErrorReporting` è presente, in [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verrà invece visualizzato l'URI indicato dal parametro `uri`.  L'URI di destinazione includerà la classe dell'eccezione esterna, la classe dell'eccezione interna e il messaggio dell'eccezione interna come parametri.  
  
 Utilizzare questo elemento per aggiungere funzionalità per la segnalazione di errori all'applicazione.  Poiché l'URI generato include informazioni sul tipo di errore, il sito Web può analizzare tali informazioni e visualizzare, ad esempio, una schermata di risoluzione dei problemi appropriata.  
  
## Esempio  
 Nel frammento seguente viene illustrato l'elemento `customErrorReporting`, insieme all'URI generato che potrebbe produrre.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## Vedere anche  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)