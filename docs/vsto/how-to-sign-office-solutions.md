---
title: 'Procedura: firmare soluzioni Office | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 12a367b6051f7ed1ca1f51e0c9d7e8ada4be4ba6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-sign-office-solutions"></a>Procedura: firmare soluzioni Office
  Se si firma una soluzione, è possibile concedere l'attendibilità alla soluzione mediante il certificato come prova. È possibile utilizzare lo stesso certificato per più soluzioni e tutte le soluzioni saranno attendibili senza aggiornamenti di criteri di sicurezza aggiuntiva.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se si modifica manualmente l'applicazione e i manifesti di distribuzione utilizzando la generazione e modifica di manifesti (mage.exe e mageui.exe), è necessario firmare nuovamente i manifesti prima di utilizzarli. Per altre informazioni, vedere [How to: Re-sign Application and Deployment Manifests](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="signing-by-using-a-certificate"></a>Utilizzando un certificato di firma  
 Un certificato è un file che contiene una chiave univoca e l'identità del server di pubblicazione di soluzioni. È possibile acquistare certificati da un'autorità di certificazione o creare un certificato personalizzato e un'autorità di certificazione firmarlo.  
  
 Visual Studio firma con un certificato temporaneo per abilitare il debug di soluzioni Office. Non utilizzare il certificato temporaneo nelle soluzioni distribuite come evidenza.  
  
#### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Per accedere a una soluzione Office usando un certificato  
  
1.  Nel **progetto** menu, fare clic su *SolutionName***proprietà**.  
  
2.  Fare clic sulla scheda **Firma**.  
  
3.  Selezionare **firmare i manifesti ClickOnce**.  
  
4.  Individuare il certificato, fare clic su **seleziona da archivio** o **seleziona da File** e passare al certificato.  
  
5.  Per verificare che venga utilizzato il certificato corretto, fare clic su **più dettagli** per visualizzare le informazioni sul certificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Pagina Firma, Creazione progetti](/visualstudio/ide/reference/signing-page-project-designer)  
  
  