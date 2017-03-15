---
title: "&lt;dependency&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#osVersionInfo"
  - "urn:schemas-microsoft-com:asm.v2#os"
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#dependency"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
  - "urn:schemas-microsoft-com:asm.v2#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<dependency> element [ClickOnce deployment manifest]"
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 27
---
# &lt;dependency&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica la versione dell'applicazione da installare e il percorso del manifesto dell'applicazione.  
  
## Sintassi  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
      <hash>  
         <dsig:Transforms>  
            <dsig:Transform  
                Algorithm  
            />  
         </dsig:Transforms>  
         <dsig:DigestMethod />  
         <dsig:DigestValue>  
         </dsig:DigestValue>  
      </hash>  
  
   </dependentAssembly>   
</dependency>  
```  
  
## Elementi e attributi  
 L'elemento `dependency` è obbligatorio  Non dispone di attributi.  A un manifesto di distribuzione possono essere associati più elementi `dependency`.  
  
 L'elemento `dependency` descrive in genere le dipendenze dell'applicazione principale dagli assembly contenuti in un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Se l'applicazione Main.exe utilizza un assembly denominato DotNetAssembly.dll, quest'ultimo deve essere elencato in una sezione delle dipendenze.  Una dipendenza può tuttavia descrivere anche altri tipi di dipendenze, ad esempio le dipendenze da una versione specifica di Common Language Runtime, da un assembly presente nella Global Assembly Cache \(GAC\) o da un oggetto COM.  Poiché [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è una tecnologia di distribuzione in modalità autonoma, non è in grado di avviare il download e l'installazione di questi tipi di dipendenze, ma impedisce che l'applicazione venga eseguita se non sono presenti tutte le dipendenze specificate.  
  
## dependentAssembly  
 Obbligatorio.  Questo elemento contiene l'elemento `assemblyIdentity`.  Nella tabella riportata di seguito sono indicati gli attributi supportati da `dependentAssembly`.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`preRequisite`|Parametro facoltativo.  Specifica che l'assembly deve già essere presente nella Global Assembly Cache.  I valori validi sono `true` e `false`.  Se l'attributo è impostato su `true` e l'assembly specificato non è presente nella Global Assembly Cache, l'applicazione non verrà eseguita.|  
|`visible`|Parametro facoltativo.  Identifica l'identità di applicazione di livello superiore, incluse le relative dipendenze.  Questo attributo viene utilizzato internamente da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per gestire l'archiviazione e l'attivazione dell'applicazione.|  
|`dependencyType`|Obbligatorio.  Specifica la relazione tra questa dipendenza e l'applicazione.  I valori validi sono:<br /><br /> -   `install`.  Il componente rappresenta un'installazione distinta dall'applicazione corrente.<br />-   `preRequisite`.  Il componente è richiesto dall'applicazione corrente.|  
|`codebase`|Parametro facoltativo.  Percorso completo del manifesto dell'applicazione.|  
|`size`|Parametro facoltativo.  Dimensione del manifesto dell'applicazione in byte.|  
  
## assemblyIdentity  
 Obbligatorio.  Questo elemento è figlio dell'elemento `dependentAssembly`.  Il contenuto di `assemblyIdentity` deve corrispondere a quello descritto nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Nella tabella riportata di seguito sono indicati gli attributi dell'elemento `assemblyIdentity`.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio.  Identifica il nome dell'applicazione.|  
|`Version`|Obbligatorio.  Specifica il numero di versione dell'applicazione nel seguente formato: `principale.secondario.build.revisione`.|  
|`publicKeyToken`|Obbligatorio.  Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del valore hash SHA\-1 della chiave pubblica utilizzata per firmare l'applicazione o l'assembly.  La lunghezza minima della chiave pubblica utilizzata per la firma deve essere di 2048 bit.|  
|`processorArchitecture`|Obbligatorio.  Specifica il tipo di microprocessore.  I valori validi sono `x86` per Windows a 32 bit e `IA64` per Windows a 64 bit.|  
|`Language`|Parametro facoltativo.  Identifica i codici di lingua in due parti dell'assembly,  ad esempio EN\-US che rappresenta l'inglese americano.  L'impostazione predefinita è `neutral`.  Questo elemento è presente nello spazio dei nomi `asmv2`.|  
|`type`|Parametro facoltativo.  Per garantire la compatibilità con le versioni precedenti della tecnologia di installazione affiancata di Windows.  L'unico valore consentito è `win32`.|  
  
## hash  
 `hash` è un elemento figlio facoltativo dell'elemento `file`.  L'elemento `hash` non contiene attributi.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizza un hash algoritmico di tutti i file contenuti in un'applicazione come controllo di sicurezza per garantire che nessun file venga modificato dopo la distribuzione.  Se l'elemento `hash` non viene incluso, questo controllo non verrà eseguito. Pertanto, non è consigliabile omettere l'elemento `hash`.  
  
## dsig:Transforms  
 L'elemento `dsig:Transforms` è un elemento figlio obbligatorio di `hash`.  L'elemento `dsig:Transforms` non contiene attributi.  
  
## dsig:Transform  
 L'elemento `dsig:Transform` è un elemento figlio obbligatorio di `dsig:Transforms`.  Nella tabella riportata di seguito sono indicati gli attributi dell'elemento `dsig:Transform`.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|Algoritmo usato per calcolare la classificazione di questo file.  L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## dsig:DigestMethod  
 L'elemento `dsig:DigestMethod` è un elemento figlio obbligatorio di `hash`.  Nella tabella riportata di seguito sono indicati gli attributi dell'elemento `dsig:DigestMethod`.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|Algoritmo usato per calcolare la classificazione di questo file.  L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## dsig:DigestValue  
 L'elemento `dsig:DigestValue` è un elemento figlio obbligatorio di `hash`.  L'elemento `dsig:DigestValue` non contiene attributi.  Il relativo valore di testo rappresenta l'hash calcolato per il file specificato.  
  
## Note  
 I manifesti di distribuzione hanno in genere un solo elemento `assemblyIdentity` che identifica il nome e la versione del manifesto dell'applicazione.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato un elemento `dependency` presente in un manifesto della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene specificata una dipendenza da un assembly già installato nella Global Assembly Cache.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene specificata una dipendenza da una versione specifica di Common Language Runtime.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene specificata una dipendenza del sistema operativo.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## Vedere anche  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)