---
title: Anatomia di un pacchetto VSIX | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 15
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
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 633db03670180ac83c5c936f66953fb38d4ebd67
ms.lasthandoff: 02/22/2017

---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia di un pacchetto VSIX
Un pacchetto VSIX è un file con estensione VSIX che contiene uno o più estensioni di Visual Studio, insieme a Visual Studio viene utilizzato per classificare e installare le estensioni dei metadati. Tali metadati sono contenuti nel manifesto VSIX e il file XML [Content_Types]. Un pacchetto VSIX può inoltre contenere uno o più file vsixlangpack per fornire il testo di programma di installazione localizzato e può contenere altri pacchetti VSIX per installare le dipendenze.  
  
 Il formato del pacchetto VSIX segue lo standard Open Packaging Conventions (OPC). Il pacchetto contiene i file binari e i file di supporto, insieme a un file con estensione XML [Content_Types] e un'estensione VSIX file manifesto. Un pacchetto VSIX può contenere l'output di più progetti, o anche più pacchetti che contengono i propri manifesti.  
  
> [!NOTE]
>  I nomi dei file inclusi nei pacchetti VSIX non devono includere spazi, né caratteri che sono riservati in identificatori URI (Uniform Resource), come definito in [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Il manifesto VSIX  
 Il manifesto VSIX contiene informazioni sull'installazione di estensione e segue lo Schema VSX. Per ulteriori informazioni, vedere [riferimento 1.0 allo Schema di estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Per un esempio di manifesto VSIX, vedere [PackageManifest elemento (elemento radice, schema VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Il manifesto VSIX deve essere denominato `extension.vsixmanifest` quando è incluso in un file con estensione VSIX.  
  
## <a name="the-content"></a>Il contenuto  
 Un pacchetto VSIX può includere modelli, gli elementi della casella degli strumenti, package VS o qualsiasi altro tipo di estensione supportata da Visual Studio.  
  
## <a name="language-packs"></a>Language Pack  
 Un pacchetto VSIX può contenere uno o più file vsixlangpack per fornire il testo localizzato durante l'installazione. Per ulteriori informazioni, vedere [localizzazione pacchetti VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Dipendenze e riferimenti  
 Un pacchetto VSIX può contenere altri pacchetti VSIX come riferimenti. Ognuno di questi altri pacchetti deve includere un manifesto VSIX proprio.  
  
 Se un utente tenta di installare un'estensione con dipendenze, il programma di installazione verifica che gli assembly necessari siano installati nel sistema dell'utente. Se gli assembly necessari non vengono trovati, **estensioni e aggiornamenti** Visualizza un elenco di assembly mancante.  
  
 Se il manifesto dell'estensione include uno o più [riferimento](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) elementi **estensioni e aggiornamenti** confronta il manifesto di ogni riferimento per le estensioni installate nel sistema e installa l'estensione di cui viene fatto riferimento, se non è già installato. Se è installata una versione precedente di un'estensione di cui viene fatto riferimento, la versione più recente sostituisce.  
  
 Se un progetto in una soluzione multiprogetto include un riferimento a un altro progetto nella stessa soluzione, il pacchetto VSIX include le dipendenze del progetto. È possibile eseguire l'override di questo comportamento facendo riferimento per il progetto interno, quindi il **proprietà** finestra, l'impostazione di **Output gruppi inclusi nel pacchetto VSIX** proprietà `BuiltProjectOutputGroup`.  
  
 Per includere le DLL satellite da assembly di riferimento nel pacchetto VSIX, aggiungere `SatelliteDllsProjectOutputGroup` per il **Output gruppi inclusi nel pacchetto VSIX** proprietà.  
  
## <a name="installation-location"></a>Percorso di installazione  
 Durante l'installazione, **estensioni e aggiornamenti** Cerca il contenuto del pacchetto VSIX in una cartella in % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Per impostazione predefinita, l'installazione si applica solo all'utente corrente, in quanto % LocalAppData % è una directory specifiche dell'utente. Tuttavia, se si imposta la [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) elemento del manifesto per `True`, verrà installato l'estensione in... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions e sarà disponibile a tutti gli utenti del computer.  
  
## <a name="contenttypesxml"></a>[Content_Types]. Xml  
 Il file XML [Content_Types] identifica i tipi di file nel file con estensione VSIX espanso. Visual Studio utilizza questo file durante l'installazione del pacchetto, ma non viene installato il file stesso. Per ulteriori informazioni su questo file, vedere [della struttura di File XML [Content_types]](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Un file con estensione XML [Content_Types] è necessario per la standard Open Packaging Conventions (OPC). Per ulteriori informazioni su OPC, vedere [OPC: un nuovo Standard per la creazione di pacchetti di dati](http://go.microsoft.com/fwlink/?LinkID=148207) sul sito Web MSDN.
