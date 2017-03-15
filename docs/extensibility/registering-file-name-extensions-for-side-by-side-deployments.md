---
title: Registrazione di estensioni di File per le distribuzioni Side-By-Side | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 13
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
ms.openlocfilehash: 216fb4cc449e8a67178f587b0c199864d267ccf4
ms.lasthandoff: 02/22/2017

---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrazione di estensioni di File per le distribuzioni Side-By-Side
Per i package VS distribuito in un ambiente side-by-side, è necessario registrare le estensioni di file per associare i file con la versione corretta di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A meno che non si utilizza un'estensione di file specifici della versione, la registrazione consente agli utenti di aprire il progetto e file di elementi nella versione appropriata del progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Sulle estensioni di File](../extensibility/about-file-name-extensions.md)  
 Viene descritto come estensioni di file registrate.  
  
 [Specifica i gestori di File per le estensioni di File](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Fornisce informazioni su come registrare le applicazioni che è possono aprire, modifica e così via, un'estensione particolare.  
  
 [La registrazione di verbi di estensioni di File](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Viene descritto come registrare verbi.  
  
 [La gestione delle associazioni di File Side-by-Side](../extensibility/managing-side-by-side-file-associations.md)  
 Viene descritto come gestire le installazioni side-by-side in cui una particolare versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve essere richiamato per aprire un file.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Descrive i problemi relativi a più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e il pacchetto Visual Studio durante lo sviluppo e distribuzione agli utenti finali.
