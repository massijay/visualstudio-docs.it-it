---
title: Registrazione e la selezione (origine controllo VSPackage) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 693955c38d4d53418a92357e54bfc7c2965bdc3e
ms.lasthandoff: 02/22/2017

---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrazione e la selezione (origine controllo VSPackage)
Un controllo del codice sorgente VSPackage deve essere registrato per esporla al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se più di un controllo del codice sorgente VSPackage è registrato, l'utente può selezionare quali VSPackage da caricare in momenti appropriati. Vedere [package VS](../../extensibility/internals/vspackages.md) per ulteriori informazioni su package VS e come eseguirne la registrazione.  
  
## <a name="registering-a-source-control-package"></a>Registrazione di un pacchetto di controllo di origine  
 Il pacchetto di controllo di origine viene registrato in modo che il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente può trovare e query per le funzionalità supportate. Questo è conforme a uno schema di caricamento ritardato in cui viene creata un'istanza di un pacchetto solo quando la funzionalità o i comandi sono necessari o richieste in modo esplicito.  
  
 Package VS inserire informazioni in una chiave del Registro di sistema specifici della versione, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*y*, dove *X* è il numero di versione principale e *Y* è il numero di versione secondario. Questa procedura consente di supportare l'installazione side-by-side di più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente (UI) supporta la selezione tra più sorgente installato controllo plug-in (tramite il pacchetto di scheda di controllo di origine) e controllo del codice sorgente di VSPackage. Può esistere un solo plug-in del controllo del codice sorgente active o VSPackage alla volta. Tuttavia, come descritto di seguito, l'IDE consente di alternare tra plug-in del controllo codice sorgente e i package VS tramite un automatica meccanismo lo scambio di pacchetto di soluzione in base. Esistono alcuni requisiti per il controllo del codice sorgente VSPackage per abilitare questo meccanismo di selezione.  
  
### <a name="registry-entries"></a>Voci del Registro di sistema  
 Un pacchetto di controllo di origine deve tre GUID privato:  
  
-   GUID del pacchetto: Si tratta del GUID principale per il pacchetto che contiene l'implementazione di controllo di origine (denominato ID_Package in questa sezione).  
  
-   Controllo del codice sorgente GUID: Questo è un GUID per il controllo del codice sorgente utilizzato per registrare con Visual Studio origine controllo Stub VSPackage e viene utilizzato anche come un comando dell'interfaccia utente il GUID di contesto. Il servizio di controllo di origine GUID è registrato sotto il controllo del codice sorgente GUID. Nell'esempio, il controllo del codice sorgente GUID viene chiamato ID_SccProvider.  
  
-   Servizio di controllo di GUID di origine: si tratta del servizio privato GUID utilizzato da Visual Studio (denominato SID_SccPkgService in questa sezione). Inoltre, il pacchetto di controllo di origine deve definire altri GUID di VSPackages, finestre e così via.  
  
 Le seguenti voci del Registro di sistema devono essere effettuate da un controllo del codice sorgente VSPackage:  
  
|Nome della chiave|Voci|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(impostazione predefinita) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(impostazione predefinita) = rg_sz:\<nome descrittivo del pacchetto ><br /><br /> Servizio = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(impostazione predefinita) = rg_sz: #\<ID di risorsa per nome localizzato ><br /><br /> Pacchetto = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Si noti che il nome della chiave, `SourceCodeControl`, già utilizzato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e non è disponibile come opzione per \<PackageName >.)|(impostazione predefinita) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Selezione di un pacchetto di controllo di origine  
 Diverse basate su API plug-in controllo origine plug-in e i package VS possono essere registrati contemporaneamente di controllo del codice sorgente. È necessario assicurarsi che il processo di selezione di un plug-in del controllo del codice sorgente o VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica il plug-in o VSPackage al momento appropriato e rinviare il caricamento dei componenti non necessari fino a quando sono necessari. Inoltre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve rimuovere altri VSPackage inattiva, tra cui le voci di menu, finestre di dialogo e barre degli strumenti, l'interfaccia utente e visualizzare l'interfaccia utente per il package VS attivo.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Carica un controllo del codice sorgente VSPackage quando viene eseguita una qualsiasi delle seguenti operazioni:  
  
-   Soluzione è aperta (quando la soluzione nel controllo del codice sorgente).  
  
     Quando viene aperta una soluzione o un progetto nel controllo del codice sorgente, l'IDE determina il controllo del codice sorgente package VS che è stato designato per tale soluzione deve essere caricato.  
  
-   Vengono eseguiti i comandi di menu del controllo origine VSPackage.  
  
 Un controllo del codice sorgente che VSPackage deve caricare tutti i componenti che necessari solo quando effettivamente dovranno essere utilizzate (altrimenti noto come caricamento ritardato).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Lo scambio automatico basati su una soluzione VSPackage  
 È possibile scambiare manualmente i package VS controllo del codice sorgente tramite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **opzioni** della finestra di dialogo di **controllo del codice sorgente** categoria. Lo scambio automatico dei pacchetti basati su una soluzione significa che un pacchetto di controllo di origine designato per una particolare soluzione viene automaticamente impostato su attivo quando viene aperta la soluzione. Ogni pacchetto di controllo di origine deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gestisce il commutatore tra i plug-in del controllo (implementa l'API di plug-in controllo di origine) di origine e i package VS di controllo del codice sorgente.  
  
 Il pacchetto di adattatori di controllo di origine viene utilizzato per passare a qualsiasi basate su API plug-in controllo di origine del plug-in. Il processo di passaggio per il pacchetto della scheda controllo origine intermedi e determinare quale plug-in del controllo del codice sorgente deve essere impostato su attivo o inattivo è trasparente all'utente. Il pacchetto di Adapter è sempre attivo quando è attiva qualsiasi plug-in del controllo del codice sorgente. Passaggio tra due quantità di plug-in di controllo di origine semplicemente il caricamento e lo scaricamento della DLL plug-in. Passaggio a un controllo del codice sorgente VSPackage, tuttavia, implica l'interazione con l'IDE per caricare il VSPackage appropriato.  
  
 Un controllo del codice sorgente VSPackage viene chiamato quando viene aperta una soluzione e la chiave del Registro di sistema per il package VS è nel file della soluzione. Quando viene aperta la soluzione, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rileva che il valore del Registro di sistema e carica il controllo del codice sorgente appropriato VSPackage. Controllo del codice sorgente tutti i package VS deve disporre le voci del Registro di sistema descritte in precedenza. Una soluzione di controllo del codice sorgente viene contrassegnata come essere associato a un controllo del codice sorgente VSPackage. Package VS deve implementare controllo del codice sorgente di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>per abilitare automatico basati su una soluzione VSPackage la sostituzione.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfaccia utente per la selezione di pacchetto e passare a Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce un'interfaccia utente di controllo del codice sorgente VSPackage e selezione plug-in di **opzioni** della finestra di dialogo di **controllo del codice sorgente** categoria. Consente all'utente di selezionare il controllo del codice sorgente active plug-in o un VSPackage. Include un elenco a discesa:  
  
-   Tutti i pacchetti di controllo di origine installati  
  
-   Tutti i plug-in del controllo origine installati  
  
-   "none" opzione che consente di disattivare controllo del codice sorgente  
  
 È visibile solo l'interfaccia utente per la scelta del controllo origine attiva. La selezione di VSPackage nasconde l'interfaccia utente per il VSPackage precedente e illustra l'interfaccia utente per uno nuovo. VSPackage attivo viene selezionato in ogni utente. Se un utente dispone di più copie di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aperte contemporaneamente, ciascuno di essi può utilizzare un VSPackage active diversi. Se più utenti sono connessi allo stesso computer, ogni utente può disporre istanze separate di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aprire, ognuno con un VSPackage active diversi. Quando più istanze di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono chiusi da un utente, il controllo del codice sorgente package VS che era attivo per l'ultima soluzione aprire diventa il controllo del codice sorgente predefinito VSPackage, l'impostazione attiva al riavvio.  
  
 Diversamente dalle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], riavviare l'IDE non è l'unico modo per passare il codice sorgente di VSPackage. Selezione di VSPackage è automatica. Commutazione di pacchetti richiede privilegi di utente di Windows (non Administrator o Power User).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)   
 [Creazione di plug-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Package VS](../../extensibility/internals/vspackages.md)
