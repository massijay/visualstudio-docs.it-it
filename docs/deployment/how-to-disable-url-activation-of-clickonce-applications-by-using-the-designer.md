---
title: 'Procedura: disabilitare l''attivazione dell''URL di applicazioni ClickOnce tramite la finestra di progettazione | Documenti Microsoft'
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
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f694b7bf80d15fa3674d64bb7d062cdf0953c14b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Procedura: disabilitare gli URL di applicazioni ClickOnce tramite la finestra di progettazione
In genere, un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione verrà avviata automaticamente subito dopo l'installazione da un server Web. Per motivi di sicurezza, è possibile scegliere di disabilitare questo comportamento e indicare agli utenti di avviare l'applicazione dal **avviare** menu invece. La procedura seguente descrive come disabilitare l’attivazione dell’URL.  
  
 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installate nel computer dell'utente da un server Web. E non può essere utilizzato per le applicazioni solo online, che possono essere avviate solo utilizzando l'URL. Per ulteriori informazioni sulla differenza tra le applicazioni solo online e installate, vedere [scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Questa procedura utilizza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È inoltre possibile eseguire questa attività utilizzando la [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Per ulteriori informazioni, vedere [procedura: disabilitare l'attivazione URL di applicazioni di ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Per disabilitare l'attivazione dell'URL per l'applicazione  
  
1.  Fare doppio clic sul nome del progetto in **Esplora**, fare clic su **proprietà**.  
  
2.  Nel **proprietà** pagina, fare clic su di **pubblica** scheda.  
  
3.  Fare clic su **Opzioni**.  
  
4.  Fare clic su **manifesti**.  
  
5.  Selezionare la casella di controllo **blocco attivazione tramite un URL dell'applicazione**.  
  
6.  Distribuire l'applicazione,  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)