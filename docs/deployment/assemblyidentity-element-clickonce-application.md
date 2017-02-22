---
title: "&lt;assemblyIdentity&gt; Element (ClickOnce Application) | Microsoft Docs"
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
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assemblyIdentity> element [ClickOnce application manifest]"
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;assemblyIdentity&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica l'applicazione distribuita in una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## Sintassi  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## Elementi e attributi  
 L'elemento `assemblyIdentity` è obbligatorio  Non contiene elementi figlio e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio.  Identifica il nome dell'applicazione.<br /><br /> Se nell'attributo `Name` sono contenuti caratteri speciali, ad esempio virgolette singole o doppie, è possibile che l'attivazione dell'applicazione abbia esito negativo.|  
|`Version`|Obbligatorio.  Specifica il numero di versione dell'applicazione nel seguente formato: `principale.secondario.build.revisione`.|  
|`publicKeyToken`|Parametro facoltativo.  Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del valore hash `SHA-1` della chiave pubblica utilizzata per firmare l'applicazione o l'assembly.  La lunghezza minima della chiave pubblica utilizzata per firmare il catalogo deve essere di 2048 bit.<br /><br /> Anche se la firma di un assembly è un'operazione consigliata ma facoltativa, questo attributo è obbligatorio.  Se un assembly non è firmato, è necessario copiare un valore da un assembly autofirmato oppure utilizzare un valore fittizio costituito da zeri.|  
|`processorArchitecture`|Obbligatorio.  Specifica il tipo di processore.  I valori validi sono `msil` per tutti i processori, `x86` per Windows a 32 bit, `IA64` per Windows a 64 bit e `Itanium` per i processori Itanium a 64 bit Intel.|  
|`language`|Obbligatorio.  Identifica i codici di lingua in due parti \(ad esempio, `it-IT`\) dell'assembly.  Questo elemento è presente nello spazio dei nomi `asmv2`.  Se non viene specificato, il valore predefinito è `neutral`.|  
  
## Esempi  
  
### Descrizione  
 Nell'esempio di codice seguente viene illustrato un elemento `assemblyIdentity` presente in un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  L'esempio di codice fa parte di un esempio più esaustivo fornito in [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### Codice  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-deployment.md)