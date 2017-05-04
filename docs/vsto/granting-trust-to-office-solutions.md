---
title: "Concessione dell&#39;attendibilit&#224; alle soluzioni Office | Microsoft Docs"
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
  - "sicurezza [sviluppo per Office in Visual Studio], attendibilità"
  - "elenchi di inclusione [sviluppo per Office in Visual Studio], informazioni sugli elenchi di inclusione"
  - "attendibilità [sviluppo per Office in Visual Studio], Office System 2007"
  - "concessione dell'attendibilità [sviluppo per Office in Visual Studio]"
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Concessione dell&#39;attendibilit&#224; alle soluzioni Office
  Concedere l'attendibilità alle soluzioni Office comporta la modifica dei criteri di sicurezza di ogni computer di destinazione in modo che l'assembly, il manifesto dell'applicazione, il manifesto di documento della soluzione.  L'attendibilità può essere concessa alla soluzione Office è o dall'utente finale.  
  
 È possibile concedere attendibilità totale alla soluzione Office la firma dei manifesti di applicazione e di distribuzione.  
  
 Gli utenti finali possono concedere l'attendibilità alla soluzione Office utilizzando una decisione sulla richiesta di attendibilità [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Attendibili di soluzione la firma dei manifesti di applicazione e di distribuzione  
 Tutti i manifesti di applicazione e di distribuzione delle soluzioni Office devono essere firmati con un certificato che identifica l'autore.  I certificati forniscono una base per prendere decisioni sull'attendibilità.  
  
 Viene creato un certificato temporaneo a cui in fase di compilazione viene concessa l'attendibilità per consentire contemporaneamente sia l'esecuzione sia il debug della soluzione.  Se si pubblica una soluzione che è firmata con un certificato temporaneo, l'utente finale sarà necessario prendere una decisione su.  
  
 Se si utilizza un certificato noto e attendibile per firmare la soluzione, quest'ultima verrà installata automaticamente senza che all'utente finale venga richiesto di prendere una decisione sull'attendibilità.  Per ulteriori informazioni su come ottenere un certificato per la firma, vedere [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  Una volta ottenuto, il certificato deve essere aggiunto all'elenco degli autori attendibili affinché venga considerato attendibile in modo esplicito.  Per ulteriori informazioni, vedere [How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications](~/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
 Se uno sviluppatore firma la soluzione con un certificato temporaneo, un amministratore può firmare nuovamente la personalizzazione con un certificato noto e attendibile utilizzando lo strumento per la generazione e la modifica di manifesti \(mage.exe\), che è uno degli strumenti di Microsoft .NET Framework.  Per ulteriori informazioni sulla firma delle soluzioni, vedere [Procedura: firmare soluzioni Office](../vsto/how-to-sign-office-solutions.md) e [Procedura: firmare manifesti dell'applicazione e di distribuzione](~/ide/how-to-sign-application-and-deployment-manifests.md).  
  
##  <a name="TrustPrompt"></a> Attendibili di soluzione tramite la richiesta di attendibilità ClickOnce  
 Se non è stato definito alcun criterio a livello di organizzazione che garantisca l'attendibilità del certificato della soluzione, [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiede all'utente finale di prendere la decisione sull'attendibilità.  Se l'utente finale concede l'attendibilità alla soluzione, il sistema crea una voce di elenco di inclusione contenente un URL e una chiave pubblica per archiviare la decisione sull'attendibilità presa.  Quando in seguito viene eseguita una personalizzazione attendibile, l'utente finale non riceverà nuove richieste.  
  
 Gli amministratori possono disabilitare la richiesta di attendibilità di [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] oppure imporre che la richiesta di attendibilità riguardi solo le soluzioni firmate con un certificato Authenticode.  Per ulteriori informazioni su come modificare queste impostazioni per le aree Risorse del computer, Intranet locale, Internet, Siti attendibili e Siti non attendibili, vedere [How to: Configure the ClickOnce Trust Prompt Behavior](~/deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Concessione dell'attendibilità ai documenti](../vsto/granting-trust-to-documents.md)   
 [Risoluzione dei problemi relativi alla sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)   
 [Considerazioni specifiche sulla sicurezza per le soluzioni Office](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  