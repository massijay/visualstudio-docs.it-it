---
title: 'Procedura: versione di pubblicazione ClickOnce Set | Documenti Microsoft'
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
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: be66edb3880e8ef91f8fd95d7f11fe465322451f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Procedura: impostare la versione pubblicazione per un'applicazione ClickOnce
Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` proprietà determina se l'applicazione che si sta pubblicando verrà considerata un aggiornamento. Viene incrementato ogni versione della fase, l'applicazione verrà pubblicata come aggiornamento.  
  
 Il `Publish Version` proprietà può essere impostata sul **pubblica** pagina del **progettazione**.  
  
> [!NOTE]
>  È disponibile un'opzione di progetto che consente di incrementare automaticamente il `Publish Version` proprietà ogni volta che l'applicazione viene pubblicata; questa opzione è abilitata per impostazione predefinita. Per ulteriori informazioni, vedere [procedura: incrementare automaticamente la versione di pubblicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Per modificare la versione di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic su di **pubblica** scheda.  
  
3.  In **versione pubblicazione** campo, incrementare la **principali**, **secondaria**, **compilare**, o **revisione** versione numeri.  
  
    > [!NOTE]
    >  È non necessario diminuire mai un numero di versione; In questo modo è possibile che il comportamento di aggiornamento imprevedibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Procedura: pubblicare versione automaticamente incremento ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)