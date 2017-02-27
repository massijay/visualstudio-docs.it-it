---
title: "&lt;assemblyIdentity&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assemblyIdentity> element [ClickOnce deployment manifest]"
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# &lt;assemblyIdentity&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica l'assembly primario dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## Sintassi  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## Elementi e attributi  
 L'elemento `assemblyIdentity` è obbligatorio  Non contiene elementi figlio e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio.  Identifica il nome leggibile della distribuzione per scopi informativi.<br /><br /> Se nell'attributo `name` sono contenuti caratteri speciali, ad esempio virgolette singole o doppie, è possibile che l'attivazione dell'applicazione abbia esito negativo.|  
|`version`|Obbligatorio.  Specifica il numero di versione dell'assembly nel seguente formato: `principale.secondario.build.revisione`.<br /><br /> Questo valore deve essere incrementato in un manifesto aggiornato per attivare un aggiornamento dell'applicazione.|  
|`publicKeyToken`|Obbligatorio.  Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del valore hash SHA\-1 della chiave pubblica utilizzata per firmare il manifesto di distribuzione.  La lunghezza minima della chiave pubblica utilizzata per la firma deve essere di 2048 bit.<br /><br /> Anche se la firma di un assembly è un'operazione consigliata ma facoltativa, questo attributo è obbligatorio.  Se un assembly non è firmato, è necessario copiare un valore da un assembly autofirmato oppure utilizzare un valore fittizio costituito da zeri.|  
|`processorArchitecture`|Obbligatorio.  Specifica il tipo di processore.  I valori validi sono `msil` per tutti i processori, `x86` per Windows a 32 bit, `IA64` per Windows a 64 bit e `Itanium` per i processori Itanium a 64 bit Intel.|  
|`type`|Obbligatorio.  Per garantire la compatibilità con la tecnologia di installazione affiancata di Windows.  L'unico valore consentito è `win32`.|  
  
## Note  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato un elemento `assemblyIdentity` presente in un manifesto della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  L'esempio di codice fa parte di un esempio più esaustivo fornito per l'argomento [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md).  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Vedere anche  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-application.md)