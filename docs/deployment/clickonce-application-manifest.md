---
title: "ClickOnce Application Manifest | Microsoft Docs"
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
  - "application manifests [ClickOnce]"
  - "ClickOnce, application manifests"
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# ClickOnce Application Manifest
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un manifesto di applicazione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è un file XML che descrive un'applicazione che viene distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 i manifesti dell' applicazione di[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] hanno i seguenti elementi e attributi.  
  
|Elemento|Descrizione|Attributi|  
|--------------|-----------------|---------------|  
|[\<assembly\> Element](../deployment/assembly-element-clickonce-application.md)|Obbligatorio.  Elemento di primo livello.|`manifestVersion`|  
|[\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-application.md)|Obbligatorio.  Identifica l'assembly primario dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[Elemento \< trustInfo \>](../deployment/trustinfo-element-clickonce-application.md)|Identifica i requisiti di sicurezza dell'applicazione.|Nessuno|  
|[\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md)|Obbligatorio.  Identifica il punto di ingresso del codice dell'applicazione.|`name`|  
|[\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)|Obbligatorio.  Identifica ciascuna dipendenza richiesta per l'esecuzione dell'applicazione.  Può anche identificare gli assembly che è necessario preinstallare.|Nessuno|  
|[\<file\> Element](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)|Parametro facoltativo.  Identifica ciascun file non assembly utilizzato dall'applicazione.  Può includere i dati sull'isolamento COM \(Component Object Model\) associati al file.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation\> Element](../deployment/fileassociation-element-clickonce-application.md)|Parametro facoltativo.  Identifica un'estensione di file da associare all'applicazione.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## Note  
 Il file manifesto di applicazione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identifica un'applicazione distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Per ulteriori informazioni su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vedere [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
## Percorso file  
 Un manifesto di applicazione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è specifico di una singola versione di una distribuzione.  Per questo motivo, devono essere archiviati separatamente dai manifesti di distribuzione.  Di solito vengono inseriti in una sottodirectory a cui viene assegnato un nome in base alla versione associata.  
  
 Il manifesto dell'applicazione deve essere sempre firmato prima della distribuzione.  Se si modifica un manifesto dell'applicazione manualmente, è necessario utilizzare mage.exe per firmare di nuovo tali manifesti dell'applicazione, per aggiornare il manifesto di distribuzione e quindi firmare nuovamente il manifesto di distribuzione.  Per ulteriori informazioni, vedere [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Sintassi del nome file  
 Il nome di un file manifesto di applicazione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] deve essere il nome completo e l'estensione dell' applicazione come identificato nell' elemento di `assemblyIdentity` , seguito dall' estensione manifest.  Per un manifesto dell'applicazione che fa riferimento, ad esempio, all'applicazione Example.exe verrà utilizzata la sintassi del nome di file riportata di seguito.  
  
 `example.exe.manifest`  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un manifesto per un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />  
  <application />  
  <entryPoint>  
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
  <trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />  
        <defaultAssemblyRequest permissionSetReference="Custom" />  
      </applicationRequestMinimum>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <!--  
          UAC Manifest Options  
          If you want to change the Windows User Account Control level replace the   
          requestedExecutionLevel node with one of the following.  
  
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />  
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />  
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />  
  
         If you want to utilize File and Registry Virtualization for backward   
         compatibility then delete the requestedExecutionLevel node.  
    -->  
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
  <dependency>  
    <dependentOS>  
      <osVersionInfo>  
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
      </osVersionInfo>  
    </dependentOS>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />  
    </dependentAssembly>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">  
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)