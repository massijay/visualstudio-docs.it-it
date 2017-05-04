---
title: "Concessione dell&#39;attendibilit&#224; ai documenti | Microsoft Docs"
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
  - "concessione dell'attendibilità [sviluppo per Office in Visual Studio]"
  - "elenchi di inclusione [sviluppo per Office in Visual Studio], informazioni sugli elenchi di inclusione"
  - "sicurezza [sviluppo per Office in Visual Studio], attendibilità"
  - "attendibilità [sviluppo per Office in Visual Studio], Office System 2007"
ms.assetid: 16893647-501e-4836-98af-a79a1e9de3ee
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Concessione dell&#39;attendibilit&#224; ai documenti
  Un progetto a livello di documento presenta gli stessi requisiti di sicurezza dei progetti a livello di applicazione, ovvero la firma dei manifesti con un certificato o la risposta, tramite clic, a una richiesta di attendibilità.  Inoltre, il documento o la cartella di lavoro si deve trovare in una directory definita come percorso attendibile.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Percorsi attendibili  
 Le applicazioni in [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e Office 2010 dispongono di un Centro protezione in cui gli utenti possono configurare le impostazioni di sicurezza e di privacy, come i percorsi attendibili.  Per le soluzioni Office, il computer locale è considerato un percorso attendibile. Tuttavia, a causa del rischio più elevato, alcune directory non possono mai essere considerate attendibili, come le cartelle temporanee del sistema, per ciascun utente e per Internet Explorer.  
  
 Per altre informazioni sul Centro protezione, vedere [Impostazioni e criteri di sicurezza in Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202).  Per altre informazioni su come creare, gestire, rimuovere e configurare cartelle attendibili, vedere [Configurare percorsi attendibili ed editori attendibili in Office System 2007](http://go.microsoft.com/fwlink/?LinkId=89203) e [Creazione, rimozione o modifica di un percorso attendibile per i file](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## Considerazioni sulla sicurezza per le soluzioni Office  
 Quando si determinano le cartelle da aggiungere ai percorsi attendibili, è necessario tenere in considerazione diversi aspetti relativi alla sicurezza:  
  
-   Le cartelle locali sono considerate più sicure e sono implicitamente attendibili.  I percorsi remoti, ad esempio le condivisioni file, devono essere designati come percorsi attendibili.  
  
-   Quando si aggiunge una directory ai percorsi attendibili, questa azione concede l'attendibilità totale non solo alle soluzioni Office, ma anche al codice VBA e ActiveX.  Per questo motivo, la directory radice e le cartelle Documenti non devono essere designate come attendibili.  
  
-   Anche se il documento stesso è designato come attendibile mediante l'uso di percorsi attendibili, per rendere attendibile la personalizzazione sono necessarie ulteriori autorizzazioni.  È possibile concedere attendibilità totale alla personalizzazione firmando i manifesti con un certificato, rispondendo tramite clic alla richiesta di attendibilità o installando la soluzione Office nella directory Programmi.  
  
-   È possibile archiviare il documento o la cartella di lavoro di una soluzione a livello di documento nella stessa directory dell'assembly o in una directory diversa.  Ad esempio, il documento potrebbe trovarsi in un server SharePoint e l'assembly potrebbe essere in una condivisione file di rete.  Per altre informazioni, vedere [Procedura: pubblicare una soluzione Office a livello di documento in un server SharePoint tramite ClickOnce](http://msdn.microsoft.com/it-it/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## Vedere anche  
 [Concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Risoluzione dei problemi relativi alla sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  