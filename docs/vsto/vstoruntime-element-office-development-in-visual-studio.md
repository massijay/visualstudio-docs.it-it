---
title: '&lt;vstoRuntime&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d6ac2393a5cfd27b2909fb5a5d63ff0260941e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `vstoRuntime` dello spazio dei nomi `vstav3` contiene una versione supportata del runtime di Visual Studio Tools per Office per una soluzione Office specifica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `vstoRuntime` è obbligatorio e si trova nello spazio dei nomi `vstav3` . Se una soluzione Office supporta due versioni del runtime di Visual Studio Tools per Office, nel manifesto dell'applicazione sono presenti due elementi `vstoRuntime` .  
  
 L'elemento `vstoRuntime` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`release`|Obbligatorio. La versione di rilascio del runtime di Visual Studio Tools per Office.|  
|`version`|Obbligatorio. Numero di versione del runtime di Visual Studio Tools per Office.|  
|`supportUrl`|Facoltativo. Collegamento alla posizione di installazione del runtime di Visual Studio Tools per Office.|  
  
 `vstoRuntime` non contiene elementi.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra l'elemento `vstoRuntime` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  