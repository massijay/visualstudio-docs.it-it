---
title: "&lt;dependency&gt; Element (ClickOnce Application) | Microsoft Docs"
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
  - "manifests [ClickOnce], dependency element"
  - "<dependency> element [ClickOnce application manifest]"
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 34
---
# &lt;dependency&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica una piattaforma o una dipendenza assembly necessaria per l'applicazione.  
  
## Sintassi  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
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
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## Elementi e attributi  
 L'elemento `dependency` è obbligatorio  Possono coesistere più istanze dell'elemento `dependency` nello stesso manifesto dell'applicazione.  
  
 L'elemento `dependency` non dispone di attributi e contiene gli elementi figlio riportati di seguito.  
  
### dependentOS  
 Parametro facoltativo.  Contiene l'elemento `osVersionInfo`.  Gli elementi `dependentOS` e `dependentAssembly` si escludono a vicenda. Per un elemento `dependency` è necessaria la presenza di uno solo di essi.  
  
 `dependentOS` supporta gli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`supportUrl`|Parametro facoltativo.  Specifica un URL di supporto per la piattaforma dipendente.  Questo URL viene visualizzato se viene trovata la piattaforma richiesta.|  
|`description`|Parametro facoltativo.  Descrive in forma leggibile il sistema operativo specificato dall'elemento `dependentOS`.|  
  
### osVersionInfo  
 Obbligatorio.  Questo elemento è un elemento figlio di `dependentOS` e contiene l'elemento `os`.  Non dispone di attributi.  
  
### os  
 Obbligatorio.  Questo elemento è figlio dell'elemento `osVersionInfo`.  Dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`majorVersion`|Obbligatorio.  Specifica il numero di versione principale del sistema operativo.|  
|`minorVersion`|Obbligatorio.  Specifica il numero di versione secondario del sistema operativo.|  
|`buildNumber`|Obbligatorio.  Specifica il numero di build del sistema operativo.|  
|`servicePackMajor`|Obbligatorio.  Specifica il numero principale del Service Pack del sistema operativo.|  
|`servicePackMinor`|Parametro facoltativo.  Specifica il numero secondario del Service Pack del sistema operativo.|  
|`productType`|Parametro facoltativo.  Identifica il valore del tipo di prodotto.  I valori validi sono `server`, `workstation` e `domainController`.  Ad esempio, per Windows 2000 Professional il valore di questo attributo è `workstation`.|  
|`suiteType`|Parametro facoltativo.  Identifica una suite del prodotto disponibile nel sistema o il tipo di configurazione del sistema.  I valori validi sono `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` e `terminal`.  Ad esempio, per Windows 2000 Professional il valore di questo attributo è `professional`.|  
  
### dependentAssembly  
 Parametro facoltativo.  Contiene l'elemento `assemblyIdentity`.  Gli elementi `dependentOS` e `dependentAssembly` si escludono a vicenda. Per un elemento `dependency` è necessaria la presenza di uno solo di essi.  
  
 `dependentAssembly` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`dependencyType`|Obbligatorio.  Consente di specificare il tipo di dipendenza.  I valori validi sono `preprequisite` e `install`.  Un assembly `install` viene installato con l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  L'assembly `prerequisite` deve essere presente nella Global Assembly Cache \(GAC\) prima che l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] possa essere installata.|  
|`allowDelayedBinding`|Obbligatorio.  Consente di specificare se l'assembly può essere caricato a livello di codice in fase di esecuzione.|  
|`group`|Parametro facoltativo.  Se l'attributo `dependencyType` viene impostato su `install`, designa un gruppo denominato di assembly che vengono installati solo su richiesta.  Per ulteriori informazioni, vedere [Procedura dettagliata: download di assembly su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](../Topic/Walkthrough:%20Downloading%20Assemblies%20on%20Demand%20with%20the%20ClickOnce%20Deployment%20API%20Using%20the%20Designer.md).<br /><br /> Se viene impostato su `framework` e l'attributo `dependencyType` viene impostato su `prerequisite`, designa l'assembly come parte di .NET Framework.  Nella Global Assemby Cache \(GAC\) non viene verificata la disponibilità di questo assembly quando si esegue l'installazione in [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] e versioni successive.|  
|`codeBase`|Obbligatorio quando l'attributo `dependencyType` è impostato su `install`.  Percorso dell'assembly dipendente.  Può essere un percorso assoluto o un percorso relativo rispetto alla codebase del manifesto.  Questo percorso deve essere un URI valido affinché il manifesto dell'assembly sia valido.|  
|`size`|Obbligatorio quando l'attributo `dependencyType` è impostato su `install`.  Dimensione in byte dell'assembly dipendente.|  
  
### assemblyIdentity  
 Obbligatorio.  Questo elemento è un elemento figlio di `dependentAssembly` e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio.  Identifica il nome dell'applicazione.|  
|`version`|Obbligatorio.  Specifica il numero di versione dell'applicazione nel seguente formato: `principale.secondario.build.revisione`.|  
|`publicKeyToken`|Parametro facoltativo.  Specifica una stringa esadecimale di 16 caratteri che rappresenta gli ultimi 8 byte del valore hash `SHA-1` della chiave pubblica utilizzata per firmare l'applicazione o l'assembly.  La lunghezza minima della chiave pubblica utilizzata per firmare il catalogo deve essere di 2048 bit.|  
|`processorArchitecture`|Parametro facoltativo.  Specifica il tipo di processore.  I valori validi sono `x86` per Windows a 32 bit e `I64` per Windows a 64 bit.|  
|`language`|Parametro facoltativo.  Identifica i codici di lingua in due parti dell'assembly, ad esempio IT\-IT.|  
  
### hash  
 `hash` è un elemento figlio facoltativo dell'elemento `assemblyIdentity`.  L'elemento `hash` non contiene attributi.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizza un hash algoritmico di tutti i file contenuti in un'applicazione come controllo di sicurezza per garantire che nessun file venga modificato dopo la distribuzione.  Se l'elemento `hash` non viene incluso, questo controllo non verrà eseguito. Pertanto, non è consigliabile omettere l'elemento `hash`.  
  
### dsig:Transforms  
 L'elemento `dsig:Transforms` è un elemento figlio obbligatorio di `hash`.  L'elemento `dsig:Transforms` non contiene attributi.  
  
### dsig:Transform  
 L'elemento `dsig:Transform` è un elemento figlio obbligatorio di `dsig:Transforms`.  L'elemento `dsig:Transform` dispone dei seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|Algoritmo usato per calcolare la classificazione di questo file.  L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### dsig:DigestMethod  
 L'elemento `dsig:DigestMethod` è un elemento figlio obbligatorio di `hash`.  L'elemento `dsig:DigestMethod` dispone dei seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Algorithm`|Algoritmo usato per calcolare la classificazione di questo file.  L'unico valore attualmente utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### dsig:DigestValue  
 L'elemento `dsig:DigestValue` è un elemento figlio obbligatorio di `hash`.  L'elemento `dsig:DigestValue` non contiene attributi.  Il relativo valore di testo rappresenta l'hash calcolato per il file specificato.  
  
## Note  
 Tutti gli assembly utilizzati dall'applicazione devono disporre di un elemento `dependency` corrispondente.  Gli assembly dipendenti non includono gli assembly che è necessario preinstallare nella Global Assembly Cache come assembly di piattaforma.  
  
## Esempio  
 Nell'esempio di codice seguente vengono illustrati gli elementi `dependency` presenti in un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  L'esempio di codice fa parte di un esempio più esaustivo fornito per l'argomento [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<dependency\> Element](../deployment/dependency-element-clickonce-deployment.md)