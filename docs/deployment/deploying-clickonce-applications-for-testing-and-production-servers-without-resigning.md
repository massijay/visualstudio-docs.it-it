---
title: "Deploying ClickOnce Applications For Testing and Production Servers without Resigning | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce applications, deploying without resigning"
  - "ClickOnce deployment, without resigning"
  - "application updates, ClickOnce"
  - "update location [ClickOnce]"
  - "deploymentProvider tag"
  - "manifests [ClickOnce]"
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Deploying ClickOnce Applications For Testing and Production Servers without Resigning
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrata una nuova funzionalità di ClickOnce introdotta in .NET Framework versione 3.5 che consente la distribuzione di applicazioni ClickOnce da più percorsi della rete senza riapposizione della firma o modifica dei manifesti ClickOnce.  
  
> [!NOTE]
>  La riapposizione della firma è tuttora il metodo preferito per la distribuzione di nuove versioni delle applicazioni.  Quando possibile, utilizzare questo metodo.  Per ulteriori informazioni, vedere [Mage.exe \(Strumento per la generazione e la modifica di manifesti\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
 Gli sviluppatori di terze parti e gli ISV possono scegliere questa funzionalità, agevolando l'aggiornamento delle applicazioni da parte dei clienti.  Questa funzionalità può essere utilizzata nelle situazioni seguenti:  
  
-   Quando si aggiorna un'applicazione, non alla prima installazione di un'applicazione.  
  
-   Quando esiste una sola configurazione dell'applicazione sul computer.  Ad esempio, se un'applicazione è configurata per puntare a due database diversi, non è possibile utilizzare questa funzionalità.  
  
## Esclusione di deploymentProvider dai manifesti di distribuzione  
 In .NET Framework 2.0 e .NET Framework 3.0, qualsiasi applicazione ClickOnce installata nel sistema per la disponibilità offline deve specificare un `deploymentProvider` nel manifesto di distribuzione.  Al `deploymentProvider` viene spesso fatto riferimento come percorso di aggiornamento; è il percorso nel quale ClickOnce verificherà la presenza di eventuali aggiornamenti.  Questo requisito, insieme alla necessità degli autori dell'applicazione di firmare le distribuzioni, rende difficile per un'azienda eseguire l'aggiornamento a un'applicazione ClickOnce da un fornitore o terze parti.  Rende anche più difficile distribuire la stessa applicazione da più percorsi nella stessa rete.  
  
 Con le modifiche apportate a ClickOnce in .NET Framework 3.5, è possibile per le terze parti fornire un'applicazione ClickOnce a un'altra organizzazione che può distribuire quindi l'applicazione in rete.  
  
 Per sfruttare questa funzionalità, gli sviluppatori di applicazioni ClickOnce devono escludere `deploymentProvider` dai manifesti di distribuzione.  In questo caso, quando si creano manifesti di distribuzione con Mage.exe, l'argomento `-providerUrl` verrà escluso, o è necessario assicurarsi che la casella di testo **Area di lancio** nella scheda **Manifesto dell'applicazione** sia vuota se si stanno generando manifesti di distribuzione con MageUI.exe.  
  
## deploymentProvider e aggiornamenti delle applicazioni  
 A partire da .NET Framework 3.5, non è più necessario specificare un `deploymentProvider` nel manifesto di distribuzione per distribuire un'applicazione ClickOnce per l'utilizzo online e offline.  In questo modo è supportato lo scenario in cui è necessario comprimere e firmare la distribuzione, ma che consente alle altre aziende di distribuire l'applicazione nelle proprie reti.  
  
 Il punto importante da ricordare è che le applicazioni che escludono un `deploymentProvider` non possono modificare il proprio percorso di installazione durante gli aggiornamenti, fino a che forniscono un aggiornamento che include nuovamente il tag `deploymentProvider`.  
  
 Di seguito sono riportati due esempi per chiarimento.  Nel primo esempio, si pubblica un'applicazione ClickOnce che non presenta tag `deploymentProvider` e si chiede agli utenti di installarla dall'indirizzo http:\/\/www.adatum.com\/MyApplication\/.  Se si decide di pubblicare l'aggiornamento successivo dell'applicazione da http:\/\/subdomain.adatum.com\/MyApplication\/, non sarà possibile indicarlo nel manifesto di distribuzione che risiede in http:\/\/www.adatum.com\/MyApplication\/.  Sarà possibile effettuare una delle due operazioni riportate di seguito.  
  
-   Ricordare agli utenti di disinstallare la versione precedente e installare la nuova versione dal nuovo percorso.  
  
-   Includere un aggiornamento all'indirizzo http:\/\/www.adatum.com\/MyApplication\/ comprendente un `deploymentProvider` che punta all'indirizzo http:\/\/www.adatum.com\/MyApplication\/.  Quindi, rilasciare un altro aggiornamento in un secondo momento con `deploymentProvider` che punta all'indirizzo http:\/\/subdomain.adatum.com\/MyApplication\/.  
  
 Nel secondo esempio, si pubblica un'applicazione ClickOnce che specifica `deploymentProvider` e si decide quindi di rimuoverlo.  Una volta che la nuova versione senza `deploymentProvider` è stata scaricata nei client, non sarà possibile reindirizzare il percorso utilizzato per gli aggiornamenti fino a quando non si rilascia una versione dell'applicazione in cui `deploymentProvider` sia stato ripristinato.  Come nel primo esempio, `deploymentProvider` deve puntare inizialmente al percorso di aggiornamento corrente, non al nuovo percorso.  In questo caso, se si tenta di inserire un `deploymentProvider` che fa riferimento all'indirizzo http:\/\/subdomain.adatum.com\/MyApplication\/, l'aggiornamento successivo avrà esito negativo.  
  
## Creazione di una distribuzione  
 Per istruzioni passo passo sulla creazione di distribuzioni disponibili da diversi percorsi della rete, vedere [Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## Vedere anche  
 [Mage.exe \(Strumento per la generazione e la modifica di manifesti\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)