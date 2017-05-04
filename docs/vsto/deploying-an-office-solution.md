---
title: "Distribuzione di una soluzione Office | Microsoft Docs"
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
  - "distribuzione ClickOnce [sviluppo per Office in Visual Studio], informazioni sulle distribuzioni di soluzioni ClickOnce"
  - "distribuzione ClickOnce [sviluppo per Office in Visual Studio], visualizzatore eventi"
  - "distribuzione ClickOnce [sviluppo per Office in Visual Studio], risoluzione dei problemi"
  - "distribuzione di applicazioni [sviluppo per Office in Visual Studio], visualizzatore eventi"
  - "distribuzione di applicazioni [sviluppo per Office in Visual Studio], soluzioni Office (System 2007)"
  - "distribuzione di applicazioni [sviluppo per Office in Visual Studio], risoluzione dei problemi"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], distribuzione di soluzioni Office"
  - "sviluppo per Office in Visual Studio, distribuzione di soluzioni Office"
  - "sviluppo per Office in Visual Studio, visualizzatore eventi"
  - "sviluppo per Office in Visual Studio, risoluzione dei problemi"
  - "Soluzioni Office [sviluppo per Office in Visual Studio], distribuzione"
  - "soluzioni [sviluppo per Office in Visual Studio], Office System 2007 (distribuzione di soluzioni)"
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Distribuzione di una soluzione Office
  È possibile distribuire le soluzioni Office utilizzando ClickOnce o Windows Installer.  L'utilizzo di ClickOnce consente di ridurre il numero di passaggi necessari per la distribuzione e l'aggiornamento della soluzione.  Se si utilizza Windows Installer, viene mantenuto il controllo sulla modalità di installazione della soluzione e sulle pagine del programma di installazione che vengono visualizzate quando gli utenti installano la soluzione.  
  
## Distribuzione di una soluzione tramite ClickOnce  
 Quando si effettua la distribuzione tramite ClickOnce, la soluzione viene pubblicata in una posizione centrale da cui gli utenti possono installarla ed eseguirla.  È possibile aggiornare la soluzione senza dover distribuire un nuovo programma di installazione agli utenti.  Questa opzione di distribuzione è più semplice, ma non consente di visualizzare agli utenti eventuali pagine di configurazione personalizzate.  Inoltre, le soluzioni devono essere installate più volte su qualsiasi computer con più di un utente.  Vedere [Distribuzione di una soluzione Office utilizzando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Distribuzione di una soluzione tramite Windows Installer  
 Quando una soluzione viene distribuita tramite Windows Installer, viene distribuito un programma di installazione agli utenti, il quali lo utilizzano per installare la soluzione.  Con questo programma di installazione è possibile installare una soluzione per tutti gli utenti di un computer contemporaneamente, anziché solo per l'utente corrente.  Questo tipo di distribuzione consente anche di avere un maggiore controllo sulle opzioni che vengono visualizzate agli utenti quando installano la soluzione.  Ad esempio, è possibile mostrare un contratto di licenza oppure consentire agli utenti di installare componenti specifici di una soluzione.  Tuttavia, per aggiornare la soluzione, è necessario distribuire un nuovo programma di installazione.  Vedere [Distribuzione di una soluzione Office tramite Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuzione di una soluzione Office utilizzando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Distribuzione di una soluzione Office tramite Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Risoluzione dei problemi relativi alla distribuzione di soluzioni Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  