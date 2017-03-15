---
title: "&lt;entryPoint&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<entryPoint> element [ClickOnce application manifest]"
  - "manifests [ClickOnce], entryPoint element"
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# &lt;entryPoint&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica l'assembly che deve essere eseguito quando l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene eseguita su un computer client.  
  
## Sintassi  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## Elementi e attributi  
 L'elemento `entryPoint` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v2`.  È possibile definire un solo elemento `entryPoint` in un manifesto dell'applicazione.  
  
 L'elemento `entryPoint` presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Parametro facoltativo.  Questo valore non viene utilizzato da .NET Framework.|  
  
 `entryPoint` presenta gli elementi seguenti.  
  
## assemblyIdentity  
 Obbligatorio.  Il ruolo di `assemblyIdentity` e dei relativi attributi viene definito nell'[\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 L'attributo `processorArchitecture` di questo elemento e l'attributo `processorArchitecture` definito nell'attributo `assemblyIdentity` in un'altra posizione nel manifesto dell'applicazione devono corrispondere.  
  
## commandLine  
 Obbligatorio.  Deve essere un elemento figlio dell'elemento `entryPoint`.  Non contiene elementi figlio e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`file`|Obbligatorio.  Riferimento locale all'assembly di avvio per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Questo valore non può contenere separatori di percorso barra \(\/\) o barra rovesciata \(\\\).|  
|`parameters`|Obbligatorio.  Descrive l'azione da eseguire con il punto di ingresso.  L'unico valore valido è `run`. Se viene fornita una stringa vuota, si presuppone che venga utilizzato il valore `run`.|  
  
## customHostRequired  
 Parametro facoltativo.  Se incluso, specifica che questa distribuzione contiene un componente che sarà distribuito all'interno di un host personalizzato e non è un'applicazione autonoma.  
  
 Se questo elemento è presente, gli elementi `assemblyIdentity` e `commandLine` non possono essere presenti  altrimenti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] genererà un errore di convalida durante l'installazione.  
  
 Questo elemento non ha né attributi né figli.  
  
## customUX  
 Parametro facoltativo.  Specifica che l'applicazione viene installata e gestita da un programma di installazione personalizzato e non crea una voce del menu Start, un collegamento o un voce Installazione applicazioni.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Per eseguire le operazioni di installazione, un'applicazione che include l'elemento customUX deve fornire un programma di installazione personalizzato che utilizzi la classe <xref:System.Deployment.Application.InPlaceHostingManager>.  Impossibile installare un'applicazione con questo elemento facendo doppio clic sul manifesto o sul programma di avvio automatico dei prerequisiti setup.exe.  Con il programma di installazione personalizzato è possibile creare voci del menu Start, collegamenti e voci Installazione applicazioni.  Se il programma di installazione personalizzato non crea una voce Installazione applicazioni, deve archiviare l'identificatore di sottoscrizione fornito dalla proprietà <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> e in seguito deve consentire all'utente di disinstallare l'applicazione chiamando il metodo <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A>.  Per ulteriori informazioni, vedere [Walkthrough: Creating a Custom Installer for a ClickOnce Application](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## Note  
 Questo elemento identifica l'assembly e il punto di ingresso per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Non è possibile utilizzare l'elemento `commandLine` per passare i parametri all'applicazione in fase di esecuzione.  È possibile accedere ai parametri della stringa di query per una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dall'oggetto <xref:System.AppDomain> dell'applicazione.  Per ulteriori informazioni, vedere [Procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md).  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un elemento `entryPoint` in un manifesto per un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  L'esempio di codice fa parte di un esempio più esaustivo fornito per l'argomento [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)