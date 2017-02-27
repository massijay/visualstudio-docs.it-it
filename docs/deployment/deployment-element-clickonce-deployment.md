---
title: "&lt;deployment&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#subscription"
  - "urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup"
  - "urn:schemas-microsoft-com:asm.v2#deploymentProvider"
  - "urn:schemas-microsoft-com:asm.v2#update"
  - "urn:schemas-microsoft-com:asm.v2#deployment"
  - "urn:schemas-microsoft-com:asm.v2#expiration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<deployment> element [ClickOnce deployment manifest]"
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# &lt;deployment&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica gli attributi utilizzati per la distribuzione degli aggiornamenti e l'esposizione al sistema.  
  
## Sintassi  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## Elementi e attributi  
 L'elemento `deployment` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v1`.  e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`install`|Obbligatorio.  Specifica se l'applicazione definisce una presenza nel menu di avviodi Windows e in **Installazione applicazioni** all'interno del Pannello di controllo.  I valori validi sono `true` e `false`.  Se si imposta `false`, in [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verrà sempre eseguita la versione più recente dell'applicazione dalla rete e l'elemento `subscription` non verrà riconosciuto.|  
|`minimumRequiredVersion`|Parametro facoltativo.  Specifica la versione minima dell'applicazione che è possibile eseguire sul client.  Se il numero di versione dell'applicazione è inferiore rispetto a quello specificato nel manifesto di distribuzione, l'applicazione non verrà eseguita.  I numeri di versione devono essere specificati nel formato `N.N.N.N`, dove `N` è un intero senza segno.  Se l'attributo `install` è impostato su `false`, l'attributo `minimumRequiredVersion` non deve essere impostato.|  
|`mapFileExtensions`|Parametro facoltativo.  Il valore predefinito è `false`.  Se `true`, tutti i file nella distribuzione dovranno presentare l'estensione deploy.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rimuoverà questa estensione dai file al momento del download dal server Web.  Se si pubblica l'applicazione mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], questa estensione verrà aggiunta automaticamente a tutti i file.  Questo parametro consente di scaricare tutti i file contenuti in una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] da un server Web che blocca la trasmissione dei file che terminano con estensioni non sicure, ad esempio .exe.|  
|`disallowUrlActivation`|Parametro facoltativo.  Il valore predefinito è `false`.  Se è impostato su `true`, non sarà possibile avviare un'applicazione installata facendo clic sull'URL né inserendo l'URL in Internet Explorer.  Se l'attributo `install` non è presente, questo attributo verrà ignorato.|  
|`trustURLParameters`|Parametro facoltativo.  Il valore predefinito è `false`.  Se è impostato su `true`, l'URL può contenere parametri di stringa di query da passare nell'applicazione, in modo simile agli argomenti della riga di comando che vengono passati a un'applicazione da riga di comando.  Per ulteriori informazioni, vedere [Procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md).<br /><br /> Se l'attributo `disallowUrlActivation` è impostato su `true`, l'attributo `trustUrlParameters` deve essere escluso dal manifesto o impostato in modo esplicito su `false`.|  
  
 L'elemento `deployment` contiene inoltre gli elementi figlio riportati di seguito.  
  
## sottoscrizione  
 Parametro facoltativo.  Contiene l'elemento `update`.  L'elemento `subscription` non contiene attributi.  Se l'elemento `subscription` non è presente, non verrà mai controllata la disponibilità di aggiornamenti per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Se l'attributo `install` dell'elemento `deployment` è impostato su `false`, l'elemento `subscription` verrà ignorato poiché per un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] avviata dalla rete viene sempre utilizzata la versione più recente.  
  
## update  
 Obbligatorio.  Questo elemento è un elemento figlio di `subscription` e contiene gli elementi `beforeApplicationStartup` o `expiration`.  `beforeApplicationStartup` e `expiration` non possono essere specificati nello stesso manifesto di distribuzione.  
  
 L'elemento `update` non contiene attributi.  
  
## beforeApplicationStartup  
 Parametro facoltativo.  Questo elemento è un elemento figlio di `update` e non dispone di attributi.  Se l'elemento `beforeApplicationStartup` è presente, l'applicazione verrà bloccata durante il controllo della disponibilità di aggiornamenti per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nel caso in cui il client sia online.  Se l'elemento non è presente, innanzitutto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] controllerà la disponibilità di aggiornamenti in base ai valori specificati per l'elemento `expiration`.  `beforeApplicationStartup` e `expiration` non possono essere specificati nello stesso manifesto di distribuzione.  
  
## expiration  
 Parametro facoltativo.  Questo elemento è un elemento figlio di `update` e non ha elementi figli.  `beforeApplicationStartup` e `expiration` non possono essere specificati nello stesso manifesto di distribuzione.  Quando si verifica il controllo dell'aggiornamento e viene rilevata una versione aggiornata, la nuova versione viene memorizzata nella cache mentre la versione esistente è in esecuzione.  La nuova versione viene quindi installata al successivo avvio dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 L'elemento `expiration` supporta gli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`maximumAge`|Obbligatorio.  Specifica il periodo di validità massimo dell'aggiornamento corrente trascorso il quale viene controllata la disponibilità di aggiornamenti.  L'unità di tempo è determinata dall'attributo `unit`.|  
|`unit`|Obbligatorio.  Identifica l'unità di tempo per `maximumAge`.  Le unità valide sono `hours`, `days` e `weeks`.|  
  
## deploymentProvider  
 Per .NET Framework 2.0, l'elemento è obbligatorio se il manifesto di distribuzione contiene una sezione `subscription`.  Per .NET Framework 3.5 e successive versioni, questo elemento è facoltativo e verrà impostato come valore predefinito sul percorso del server e del file in cui è stato individuato il manifesto della distribuzione.  
  
 Questo è un elemento figlio dell'elemento `deployment` e dispone dell'attributo riportato di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`codebase`|Obbligatorio.  Identifica il percorso URI \(Uniform Resource Identifier\) del manifesto di distribuzione utilizzato per l'aggiornamento dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Questo elemento consente anche di inoltrare i percorsi di aggiornamento per le installazioni basate su CD.  Deve essere un URI valido.|  
  
## Note  
 È possibile configurare l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in modo che la disponibilità di aggiornamenti venga controllata all'avvio, dopo l'avvio o non venga mai controllata.  Per controllare la disponibilità di aggiornamenti all'avvio, assicurarsi che l'elemento `beforeApplicationStartup` sia contenuto nell'elemento `update`.  Per analizzare la disponibilità di aggiornamenti dopo l'avvio, assicurarsi che l'elemento `expiration` sia presente nell'elemento `update` e che gli intervalli di aggiornamento siano stati specificati.  
  
 Per disabilitare il controllo della disponibilità di aggiornamenti, rimuovere l'elemento `subscription`.  Anche se nel manifesto di distribuzione viene specificato di non controllare mai la disponibilità di aggiornamenti, è comunque possibile eseguire tale controllo manualmente utilizzando il metodo <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>.  
  
 Per ulteriori informazioni sugli aggiornamenti di deploymentProvider, vedere [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## Esempi  
 Nell'esempio di codice seguente viene illustrato un elemento `deployment` in un manifesto della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Per indicare il percorso di aggiornamento preferito, viene utilizzato un elemento `deploymentProvider`.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## Vedere anche  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)