---
title: Registrazione di VSPackage | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 18
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
ms.openlocfilehash: bebd023d8cbecf97f75570bf57ed2cd4462ffe92
ms.lasthandoff: 02/22/2017

---
# <a name="vspackage-registration"></a>Registrazione di VSPackage
Package VS deve avvertire [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cui sono installati e deve essere caricato. Questo processo viene eseguito scrivendo informazioni nel Registro di sistema. Che è un processo tipico di un programma di installazione.  
  
> [!NOTE]
>  È una prassi durante lo sviluppo di VSPackage utilizzare registrazione automatica. Tuttavia, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partner non può essere rilasciato loro prodotti tramite registrazione automatica come parte del programma di installazione.  
  
 Le voci del Registro di sistema in un pacchetto Windows Installer vengono in genere stabilite nella tabella del Registro di sistema. È anche possibile registrare estensioni di file nella tabella del Registro di sistema. Tuttavia, Windows Installer fornisce supporto incorporato tramite l'identificatore programmatico (ProgId), classe, estensione e tabelle di verbo. Per ulteriori informazioni, vedere [tabelle di Database](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Assicurarsi che le voci del Registro di sistema associate al componente che è appropriato per la propria strategia side-by-side scelta. Ad esempio, le voci del Registro di sistema per un file condiviso devono essere associate a quel file Windows Installer. Allo stesso modo, le voci del Registro di sistema per un file specifico della versione devono essere associate a quel file. In caso contrario, installare o disinstallare il pacchetto Visual Studio per una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] potrebbe interrompere il pacchetto Visual Studio nelle altre versioni. Per ulteriori informazioni, vedere [supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Il modo più semplice per gestire la registrazione è utilizzare gli stessi dati negli stessi file per la registrazione per gli sviluppatori e registrazione in fase di installazione. Ad esempio, alcuni strumenti di sviluppo di programma di installazione possono utilizzare file in formato con estensione reg in fase di compilazione. Se gli sviluppatori di gestiscono i file. reg per sviluppo quotidiane e il debug, tali file possono essere inclusi nel programma di installazione automaticamente. Se non è possibile condividere automaticamente i dati di registrazione, è necessario che la copia del programma di installazione dei dati di registrazione sia corrente.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrazione di VS non gestito  
 Package VS non gestito (inclusi quelli generati dal pacchetto di modello di Visual Studio) utilizzare i file con estensione RGS stile ATL per archiviare le informazioni di registrazione. Il formato di file con estensione RGS è specifico di ATL e non può essere utilizzato in genere come-per un'installazione dello strumento di creazione. Informazioni di registrazione per il programma di installazione di VSPackage devono essere gestite separatamente. Ad esempio, gli sviluppatori possono sincronizzare i file nel formato con estensione reg con RGS le modifiche ai file. I file con estensione reg possono essere uniti a RegEdit per progetti di sviluppo o utilizzati da un programma di installazione.  
  
## <a name="registering-managed-vspackages"></a>Registrazione VSPackages gestito  
 Lo strumento RegPkg legge gli attributi di registrazione da un VSPackage gestito e sia possibile scrivere le informazioni direttamente al Registro di sistema o la scrittura di file con estensione reg in formato che può essere utilizzata da un programma di installazione.  
  
> [!NOTE]
>  Lo strumento RegPkg non è ridistribuibile e non può essere utilizzato per registrare un VSPackage sul sistema dell'utente.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Perché i package VS deve non effettuare la registrazione automatica in fase di installazione  
 I programmi di installazione di VSPackage non basarsi sulla registrazione automatica. A prima vista, mantenendo i valori del Registro di sistema del VSPackage solo in VSPackage stesso dovrebbe essere una buona idea. Dato che gli sviluppatori devono i valori del Registro di sistema disponibili per le operazioni di routine e di test, è opportuno evitare di mantenere una copia separata dei dati del Registro di sistema nel programma di installazione. Il programma di installazione può basarsi su VSPackage di scrivere i valori del Registro di sistema.  
  
 Buona in teoria, durante la registrazione automatica presenta diversi difetti che lo rendono appropriato per l'installazione di VSPackage:  
  
-   Corretto supporto di installazione, disinstallazione, il rollback dell'installazione e disinstallazione rollback è necessario creare quattro azioni personalizzate per ogni VSPackage gestito che esegue la registrazione automatica chiamando RegPkg.  
  
-   L'approccio adottato per il supporto side-by-side potrebbe richiedere che si creano quattro azioni personalizzate che richiamano RegSvr32 o RegPkg per ogni versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Un'installazione con i moduli di registrazione automatica non può essere annullata in modo sicuro in quanto non è possibile indicare se le chiavi di registrazione automatica vengono utilizzate da un'altra applicazione o funzionalità.  
  
-   DLL registrazione automatica collegare talvolta DLL ausiliarie che non sono presenti o sono una versione non corretta. Al contrario, Windows Installer può registrare le DLL utilizzando le tabelle del Registro di sistema senza dipendenza lo stato corrente del sistema.  
  
-   Codice di registrazione automatica è possibile negare l'accesso alle risorse di rete, quali librerie dei tipi, se un componente specificato come esecuzione dall'origine sia elencato nella tabella SelfReg. Ciò può provocare l'installazione del componente per avere esito negativo durante un'installazione amministrativa.  
  
## <a name="see-also"></a>Vedere anche  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Registrazione del pacchetto gestito](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
