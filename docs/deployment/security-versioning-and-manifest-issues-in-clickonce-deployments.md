---
title: "Security, Versioning, and Manifest Issues in ClickOnce Deployments | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "versioning, ClickOnce applications"
  - "ClickOnce applications, Windows Vista User Account Control"
  - "ClickOnce applications, versioning issues"
  - "security, ClickOnce applications"
  - "Windows 7, ClickOnce deployments"
  - "ClickOnce applications, manifest issues"
  - "User Account Control, ClickOnce applications"
  - "Windows Vista, ClickOnce deployments"
  - "manifests [ClickOnce]"
  - "ClickOnce applications, security issues"
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Security, Versioning, and Manifest Issues in ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] presenta una serie di problemi relativi alla sicurezza, al controllo delle versioni delle applicazioni e alla sintassi e alla semantica dei manifesti che possono causare la mancata riuscita di una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
## ClickOnce e controllo dell'account utente di Windows Vista  
 In [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], per impostazione predefinita le applicazioni vengono eseguite con le autorizzazioni di utente standard, anche se l'utente corrente dispone di autorizzazioni di amministratore.  Se l'esecuzione di un'azione in un'applicazione richiede autorizzazioni di amministratore, il sistema operativo richiede all'utente di immettere tali credenziali.  Questa funzionalità denominata Controllo dell'account utente \(UAC\), impedisce alle applicazioni di apportare modifiche che possono influire sull'intero sistema operativo senza l'approvazione esplicita di un utente.  Le applicazioni Windows dichiarano di richiedere tale elevazione di autorizzazioni specificando l'attributo `requestedExecutionLevel` nella sezione `trustInfo` del manifesto dell'applicazione.  
  
 A causa del rischio di esporre le applicazioni agli attacchi di elevazione di sicurezza, le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non possono richiedere l'elevazione dell'autorizzazione se UAC è attivato per il client.  Qualsiasi applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che tenta di impostare l'attributo `requestedExecutionLevel` su `requireAdministrator` o su `highestAvailable` non verrà installata su [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  
  
 In alcuni casi, è possibile tentare l'esecuzione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con autorizzazioni di amministratore a causa della logica di rilevamento del programma di installazione su [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  In questo caso, è possibile impostare l'attributo `requestedExecutionLevel` nel manifesto dell'applicazione su `asInvoker`.  L'applicazione stessa verrà eseguita senza ricorrere all'elevazione. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] aggiungerà automaticamente tale attributo a tutti i manifesti dell'applicazione.  
  
 Se si sta sviluppando un'applicazione che richiede autorizzazioni di amministratore per l'intera durata dell'applicazione, è necessario distribuire l'applicazione utilizzando invece la tecnologia Windows Installer \(MSI\).  Per ulteriori informazioni, vedere [Nozioni di base di Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## Quote per applicazioni online e applicazioni parzialmente attendibili  
 Se l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene eseguita in modalità online anziché essere installata, è necessario che venga rispettata la quota definita per le applicazioni online.  Inoltre, un'applicazione di rete eseguita con un livello di attendibilità parziale, ad esempio con un set di autorizzazioni di sicurezza limitato, non può avere una dimensione superiore alla metà della quota.  
  
 Per ulteriori informazioni e per istruzioni su come cambiare la quota per le applicazioni online, vedere [ClickOnce Cache Overview](../deployment/clickonce-cache-overview.md).  
  
## Problemi relativi al controllo delle versioni  
 Se all'assembly sono assegnati nomi sicuri e il numero di versione dell'assembly viene incrementato in base a un aggiornamento dell'applicazione, possono verificarsi dei problemi.  Qualsiasi assembly compilato con un riferimento a un assembly con nome sicuro deve essere ricompilato, altrimenti tenterà di fare riferimento alla versione precedente.  Il tentativo viene effettuato in quanto l'assembly sta utilizzando il valore della versione precedente nella richiesta di associazione.  
  
 Si supponga, ad esempio, di disporre di un assembly con nome sicuro in un progetto separato con numero di versione 1.0.0.0  e che, una volta compilato, l'assembly venga aggiunto come riferimento al progetto contenente l'applicazione principale.  Se si aggiorna l'assembly, si incrementa il numero di versione impostando 1.0.0.1 e si tenta di distribuire l'aggiornamento senza ricompilare l'applicazione, quest'ultima non sarà in grado di caricare l'assembly in fase di esecuzione.  
  
 Questo errore può verificarsi solo se si modificano i manifesti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manualmente. Non potrà mai verificarsi se la distribuzione viene generata mediante [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## Specifica di singoli assembly .NET Framework nel manifesto  
 L'applicazione non verrà caricata se una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è stata modificata manualmente per fare riferimento a una versione precedente di un assembly [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Se ad esempio si aggiunge un riferimento all'assembly System.Net per una versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] precedente alla versione specificata nel manifesto, si verificherà un errore.  Non tentare in genere di specificare riferimenti a singoli assembly [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], poiché la versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in cui viene eseguita l'applicazione è specificata come dipendenza nel manifesto dell'applicazione.  
  
## Problemi relativi all'analisi dei manifesti  
 I file manifesto utilizzati da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono file XML il cui formato deve essere valido e corretto. In questi file devono essere rispettate le regole della sintassi XML e utilizzati solo elementi e attributi definiti nello schema XML appropriato.  
  
 Possono verificarsi problemi in un file manifesto se si seleziona per l'applicazione un nome contenente un carattere speciale, ad esempio una virgoletta singola o doppia.  Il nome dell'applicazione fa parte dell'identità [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non analizza attualmente identità che contengono caratteri speciali.  Se l'applicazione non viene attivata, assicurarsi di aver utilizzato solo caratteri alfabetici e numerici per il nome e provare a ridistribuirla.  
  
 Se i manifesti di distribuzione o dell'applicazione vengono modificati manualmente, è possibile che vengano inavvertitamente danneggiati,  impedendo così una corretta installazione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  È possibile eseguire il debug di questi errori in fase di esecuzione facendo clic su **Dettagli** nella finestra di dialogo **Errori ClickOnce** e leggendo il messaggio di errore nel log.  Verrà fornita una delle seguenti informazioni:  
  
-   La descrizione di un errore di sintassi, insieme all'indicazione del numero di riga e della posizione del carattere in cui è presente l'errore.  
  
-   Il nome di un elemento o attributo utilizzato in modo non conforme allo schema del manifesto.  Se ai manifesti è stato aggiunto manualmente del codice XML, sarà necessario confrontare le aggiunte effettuate con gli schemi dei manifesti.  Per ulteriori informazioni, vedere [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md) e [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
-   Un conflitto tra ID.  I riferimenti a dipendenze nel manifesto di distribuzione e in quello dell'applicazione devono essere univoci in tutti e due gli attributi `name` e `publicKeyToken`.  Se entrambi gli attributi corrispondono per due elementi di un manifesto, l'analisi del manifesto non avrà esito positivo.  
  
## Precauzioni relative alla modifica manuale di manifesti o applicazioni  
 Quando si aggiorna il manifesto di un'applicazione, è necessario firmare nuovamente sia il manifesto dell'applicazione che quello di distribuzione.  Il manifesto di distribuzione contiene un riferimento al manifesto dell'applicazione che include l'hash del file e la firma digitale.  
  
### Precauzioni relative all'utilizzo della proprietà deploymentProvider  
 Il manifesto di distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dispone di una proprietà `deploymentProvider` che punta al percorso completo dal quale l'applicazione deve essere installata e servita.  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Questo percorso viene impostato in fase di creazione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ed è obbligatorio per le applicazioni installate.  Si tratta del percorso standard da cui il programma di installazione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installerà l'applicazione e in cui verificherà se sono disponibili aggiornamenti.  Di conseguenza, se si utilizza il comando **xcopy** per copiare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in un percorso diverso, ma non si modifica il valore della proprietà `deploymentProvider`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] continuerà a fare riferimento al percorso originale per tentare di scaricare l'applicazione.  
  
 Se si desidera spostare o copiare un'applicazione, è necessario aggiornare anche il percorso definito nella proprietà `deploymentProvider` in modo che il client esegua effettivamente l'installazione dal nuovo percorso.  L'aggiornamento del percorso è un'operazione delicata se sono presenti applicazioni installate.  Per le applicazioni online che vengono sempre avviate tramite l'URL originale, l'impostazione della proprietà `deploymentProvider` è facoltativa.  Se `deploymentProvider` è impostata, ne verrà utilizzato il valore. In caso contrario, come URL di base per il download dei file dell'applicazione verrà utilizzato l'URL di avvio dell'applicazione.  
  
> [!NOTE]
>  Ogni volta che si aggiorna il manifesto, è necessario anche firmarlo nuovamente.  
  
## Vedere anche  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)