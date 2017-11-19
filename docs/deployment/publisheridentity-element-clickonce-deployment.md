---
title: '&lt;publisherIdentity&gt; elemento (distribuzione di ClickOnce) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 9a59b97b3260beaf39ae20b62a44903add13e622
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; elemento (distribuzione di ClickOnce)
Contiene informazioni sull'editore che ha firmato questo manifesto della distribuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `publisherIdentity` elemento è obbligatorio per manifesti firmati. Nella tabella seguente vengono illustrati gli attributi di `publisherIdentity` supportato dall'elemento.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Descrive l'identità dell'entità che ha pubblicato l'applicazione.|  
|`issuerKeyHash`|Obbligatorio. Contiene l'hash SHA-1 della chiave pubblica dell'autorità di certificazione.|  
  
#### <a name="parameters"></a>Parametri  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="subhead"></a>Sottotitolo