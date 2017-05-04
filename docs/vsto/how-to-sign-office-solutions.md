---
title: "Procedura: firmare soluzioni Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "certificati [sviluppo per Office in Visual Studio], soluzioni Office"
  - "sicurezza [sviluppo per Office in Visual Studio], firma di soluzioni Office"
  - "firma di manifesti [sviluppo per Office in Visual Studio]"
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: firmare soluzioni Office
  Se si firma una soluzione, è possibile concedere attendibilità alla soluzione utilizzando il certificato come evidenza.  È possibile utilizzare lo stesso certificato per più soluzioni e tutte le soluzioni saranno ritenute attendibili senza ulteriori aggiornamenti dei criteri di sicurezza.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se si modificano i manifesti dell'applicazione e quelli di distribuzione utilizzando lo Strumento per la generazione e la modifica di manifesti \(mage.exe e mageui.exe\), è necessario firmare nuovamente i manifesti prima che sia possibile utilizzarli.  Per ulteriori informazioni, vedere [How to: Re-sign Application and Deployment Manifests](~/deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Applicazione della firma mediante un certificato  
 Un certificato è un file che contiene una chiave univoca e l'identità dell'autore della soluzione.  È possibile acquistare certificati da un autorità di certificazione oppure creare il proprio certificato e farlo firmare da un'autorità di certificazione.  
  
 Visual Studio firma le soluzioni Office con un certificato temporaneo per abilitare il debug.  Evitare di utilizzare il certificato temporaneo come evidenza di attendibilità nelle soluzioni distribuite.  
  
#### Per firmare una soluzione Office utilizzando un certificato  
  
1.  Scegliere **Proprietà** *NomeSoluzione* dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Firma**.  
  
3.  Selezionare **Firma i manifesti ClickOnce**.  
  
4.  Trovare il certificato facendo clic su **Seleziona dall'archivio** o **Seleziona da un file** e spostandosi sul certificato.  
  
5.  Per verificare che venga utilizzato il certificato corretto, fare clic su **Altri dettagli** per visualizzare le informazioni del certificato.  
  
## Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Pagina Firma, Progettazione progetti](../ide/reference/signing-page-project-designer.md)  
  
  