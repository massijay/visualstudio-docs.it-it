---
title: 'Procedura: disabilitare l''attivazione dell''URL di applicazioni ClickOnce | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1142a047dc1e3ad74b75cf2d82432e1d2f16c1a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Procedura: disabilitare l'attivazione dell'URL delle applicazioni ClickOnce
In genere, un’applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene avviata automaticamente subito dopo l'installazione da un server Web. Per motivi di sicurezza, è possibile scegliere di disabilitare questo comportamento e indicare agli utenti di avviare l'applicazione dal **avviare** menu invece. La procedura seguente descrive come disabilitare l’attivazione dell’URL.  
  
 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installate nel computer dell'utente da un server Web. Non può essere usata per le applicazioni solo online, che possono essere avviate solo mediante l'URL. Per ulteriori informazioni sulla differenza tra le applicazioni solo online e installate, vedere [scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Utilizza questa procedura di [! INCLUDERE[winsdklong](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). È anche possibile eseguire questa procedura mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="procedure"></a>Routine  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione  
  
1.  Aprire il manifesto della distribuzione in MageUI.exe. Se non ancora stato creato uno, seguire i passaggi in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Selezionare il **opzioni di distribuzione** scheda.  
  
3.  Cancella il **Esegui automaticamente l'applicazione dopo l'installazione** casella di controllo.  
  
4.  Salvare e firmare il manifesto.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)