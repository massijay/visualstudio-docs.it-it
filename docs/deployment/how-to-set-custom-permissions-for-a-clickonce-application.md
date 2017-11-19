---
title: 'Procedura: impostare le autorizzazioni personalizzate per un''applicazione ClickOnce | Documenti Microsoft'
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
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 0e99583b9222e71421e548b0cdf1338e81c3c45b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Procedura: impostare le autorizzazioni personalizzate per un'applicazione ClickOnce
È possibile distribuire un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che usa le autorizzazioni predefinite per le aree Internet o Intranet locale. In alternativa, è possibile creare un'area personalizzata per le autorizzazioni specifiche necessarie all'applicazione. È possibile eseguire questa operazione personalizzando le autorizzazioni di sicurezza nella pagina **Sicurezza** di **Creazione progetti**.  
  
### <a name="to-customize-a-permission"></a>Per personalizzare un'autorizzazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Sicurezza** .  
  
3.  Selezionare la casella di controllo **Abilita impostazioni di sicurezza ClickOnce** .  
  
4.  Selezionare il pulsante di opzione **È un'applicazione con attendibilità parziale** .  
  
     I controlli nella sezione **Autorizzazioni di sicurezza ClickOnce** sono abilitati.  
  
5.  Dall'elenco a discesa **Area da cui verrà installata l'applicazione** selezionare **(Personalizzata)**.  
  
6.  Fare clic su **Modifica XML autorizzazioni**.  
  
     Il file app.manifest verrà aperto nell'Editor XML.  
  
7.  Prima dell'elemento `</applicationRequestMinimum>` , aggiungere il codice XML per le autorizzazioni richieste dall'applicazione.  
  
    > [!NOTE]
    >  È possibile usare il metodo `ToXml` di un set di autorizzazioni per generare il codice XML per il manifesto dell'applicazione. Ad esempio, per generare il codice XML per il set di autorizzazioni <xref:System.Security.Permissions.EnvironmentPermission> , chiamare il metodo <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> . Per altre informazioni sulla struttura del codice XML del set di autorizzazioni, vedere [NIB: How to: Import a Permission Set by Using an XML File](http://msdn.microsoft.com/en-us/dea16b54-c108-408a-ac36-cdc05f746236)(Procedura: Importare un set di autorizzazioni usando un file XML).  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per le applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sicurezza di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)