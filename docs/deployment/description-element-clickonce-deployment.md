---
title: "&lt;description&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#description"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<description> element [ClickOnce deployment manifest]"
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# &lt;description&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica informazioni sull'applicazione, utilizzate per creare una shell e l'elemento **Installazione applicazioni** nel Pannello di controllo.  
  
## Sintassi  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## Elementi e attributi  
 L'elemento `description` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v1`.  Non contiene elementi figlio e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`publisher`|Obbligatorio.  Identifica il nome della società utilizzato per il posizionamento delle icone nel menu **Start** di Windows e l'elemento **Installazione applicazioni** nel Pannello di controllo quando la distribuzione è configurata per l'installazione.|  
|`product`|Obbligatorio.  Identifica il nome completo del prodotto.  Utilizzato come titolo per l'icona installata nel menu **Start** di Windows.|  
|`suiteName`|Parametro facoltativo.  Identifica una sottocartella all'interno della cartella `publisher` nel menu **Start** di Windows.|  
|`supportUrl`|Parametro facoltativo.  Specifica un URL di supporto visualizzato nell'elemento **Installazione applicazioni** del Pannello di controllo.  Quando la distribuzione viene configurata per l'installazione, viene inoltre creato un collegamento a questo URL per il supporto dell'applicazione nel menu Start di Windows.|  
  
## Note  
 L'elemento della descrizione è obbligatorio in tutte le configurazioni di distribuzione.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato un elemento `description` in un manifesto della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  L'esempio di codice fa parte di un esempio più esaustivo fornito per l'argomento [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md).  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Vedere anche  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)