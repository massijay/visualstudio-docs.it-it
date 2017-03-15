---
title: Shell (Isolated o integrato) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 25
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
ms.openlocfilehash: ed0e82dbc2c093a94080fe3fcf07a3e3b20e1a50
ms.lasthandoff: 02/22/2017

---
# <a name="shell-isolated-or-integrated"></a>Shell (Isolated o integrato)
È possibile creare l'applicazione basata su Visual Studio in modalità integrata o isolata. In modalità integrata, molte funzionalità di Visual Studio sono disponibili oltre all'applicazione. In modalità isolata, si sceglie un sottoinsieme delle funzionalità di Visual Studio che si desidera distribuire insieme a un'estensione personalizzata.  
  
## <a name="integrated-mode"></a>Modalità integrata  
 La modalità integrata consente agli utenti di utilizzare le funzionalità standard di Visual Studio con gli strumenti personalizzati. La shell integrata è destinata principalmente per l'hosting di linguaggi di programmazione e strumenti di sviluppo software.  
  
 Strumenti personalizzati che vengono compilati automaticamente in base la shell integrata di tipo merge con qualsiasi altra edizione di Visual Studio è installato nello stesso computer. Se Visual Studio non è già installato, è possibile fornire una versione ridistribuibile di Visual Studio integrated shell.  
  
 La versione ridistribuibile di Visual Studio integrated shell non include linguaggi di programmazione e le funzionalità che supportano i relativi sistemi di progetto.  
  
> [!NOTE]
>  La modalità integrata di Visual Studio shell può essere installata insieme a tutte le edizioni di Visual Studio, tranne le versioni Express.  
  
 Per ulteriori informazioni, vedere [Visual Studio Shell (Integrated)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modalità isolata  
 Modalità locale consente di creare strumenti personalizzati da eseguire side-by-side con altre versioni di Visual Studio. Destinato principalmente per gli strumenti che possono accedere ai servizi di Visual Studio senza a seconda di tutte le funzionalità standard di Visual Studio. È possibile personalizzare l'aspetto delle applicazioni basate su shell di Visual Studio isolato. È facilmente possibile disattivare le funzionalità e i gruppi di comandi di menu che non si desidera che venga visualizzato insieme all'applicazione.  
  
 Per ulteriori informazioni, vedere [Visual Studio Shell isolata](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>La distribuzione dell'applicazione Shell integrata o isolato  
 Per distribuire l'applicazione shell integrata o isolato, è necessario includere l'applicazione, una speciale integrata o isolata shell redistributable e un programma di installazione. Per ulteriori informazioni sulla distribuzione e installazione, vedere [la distribuzione di applicazioni isolate Shell](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  Il [contratto di licenza utente finale (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) per Visual Studio integrato e isolata shell include una sezione sulla raccolta dati (**sezione 3. Data**).  Descrive i dati sull'utilizzo del cliente che possono essere raccolte da Microsoft agli utenti di entrambi software shell integrata o isolato che è incorporata nell'applicazione. Per ulteriori informazioni, vedere [informativa famiglia di prodotti di Microsoft Visual Studio sulla Privacy](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Se si raccolgono dati di utilizzo separato dai clienti tramite l'applicazione, è necessario fornire comunicazione agli utenti dell'applicazione di è raccogliere.  Quando si distribuisce il software di shell isolata o integrato come parte dell'applicazione, in base alla licenza di Visual Studio Software Development Kit, è necessario includere uno dei seguenti:  
>   
>  -   il contratto di licenza come parte della licenza dell'applicazione  
> -   il proprio contratto che richiede agli utenti di accettare i termini di protezione di Visual Studio integrato o isolati shell almeno della quantità come condizioni di licenza Microsoft utente finale per il software di shell  
  
## <a name="additional-resources"></a>Risorse aggiuntive  
 Per ulteriori informazioni sui pacchetti ridistribuibili, vedere il [download di Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) sito Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
