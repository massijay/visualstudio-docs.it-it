---
title: "&lt;fileAssociation&gt; Element (ClickOnce Application) | Microsoft Docs"
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
  - "<fileAssociation> element [ClickOnce application manifest]"
  - "manifests [ClickOnce], fileAssociation element"
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;fileAssociation&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica un'estensione di file da associare all'applicazione.  
  
## Sintassi  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## Elementi e attributi  
 L'elemento `fileAssociation` è facoltativo.  e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`extension`|Obbligatorio.  Estensione di file da associare all'applicazione.|  
|`description`|Obbligatorio.  Descrizione del tipo di file che verrà utilizzato dalla shell.|  
|`progid`|Obbligatorio.  Nome che identifica in modo univoco il tipo di file.|  
|`defaultIcon`|Obbligatorio.  Specifica l'icona per utilizzare per i file con questa estensione.  Il file di icona deve essere specificato utilizzando [\<file\> Element](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md) all'interno di [\<assembly\> Element](../deployment/assembly-element-clickonce-application.md) che contiene questo elemento.|  
  
## Note  
 Questo elemento deve includere un riferimento dello spazio dei nomi XML a "urn:schemas\-microsoft\-com:clickonce.v1".  Se viene utilizzato l'elemento `<fileAssociation>`, deve essere specificato dopo l'elemento `<application>` nel relativo [\<assembly\> Element](../deployment/assembly-element-clickonce-application.md) padre.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non sovrascriverà le associazioni di file esistenti.  Tuttavia, un'applicazione ClickOnce può eseguire l'override dell'estensione di file solo per l'utente corrente.  Dopo aver disinstallato l'applicazione ClickOnce, questa rimuove l'associazione file per l'utente in modo che l'associazione del singolo computer sia ancora attiva.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito vengono illustrati gli elementi `fileAssociation` in un manifesto di un'applicazione editor di testo distribuita mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  In questo esempio di codice è inoltre incluso [\<file\> Element](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md) richiesto dall'attributo `defaultIcon`.  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)