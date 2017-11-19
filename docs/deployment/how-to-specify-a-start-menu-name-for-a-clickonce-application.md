---
title: 'Procedura: specificare un nome di Menu Start per un''applicazione ClickOnce | Documenti Microsoft'
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
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: b27cf6d67cef1098a54277d4857b75d3fba0ff65
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Procedura: specificare il nome di un'applicazione ClickOnce per il menu Start
Quando un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è installata per l'utilizzo online e offline, viene aggiunta una voce di **avviare** menu e **Aggiungi / Rimuovi programmi** elenco. Per impostazione predefinita, il nome visualizzato è identico al nome dell'assembly dell'applicazione, ma è possibile modificare il nome visualizzato impostando **nome prodotto** nel **opzioni di pubblicazione** la finestra di dialogo.  
  
 **Nome del prodotto** verrà visualizzata la pagina publish.htm; per un'applicazione installata offline, sarà il nome della voce nel **avviare** menu e sarà anche il nome visualizzato in **aggiungere o rimuovere I programmi**.  
  
 **Nome dell'autore** verranno visualizzati nella pagina publish.htm **nome prodotto**, e per un'applicazione installata offline, sarà anche il nome della cartella che contiene l'icona dell'applicazione nel **avviare**  menu.  
  
 È possibile impostare il **nome prodotto** e **nome editore** proprietà nel **opzioni di pubblicazione** nella finestra di dialogo disponibile nel **pubblica** pagina del **Progettazione progetti**.  
  
### <a name="to-specify-a-start-menu-name"></a>Per specificare un nome di menu Start  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  Fare clic su di **opzioni** pulsante per aprire la **opzioni di pubblicazione** la finestra di dialogo.  
  
4.  Fare clic su **descrizione**.  
  
5.  Nel **opzioni di pubblicazione** finestra di dialogo immettere il nome da visualizzare **nome prodotto**.  
  
6.  Facoltativamente, è possibile immettere un nome di server di pubblicazione in **nome editore**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)