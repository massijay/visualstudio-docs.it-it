---
title: "How to: Specify an Alternate Location for Deployment Updates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "ClickOnce deployment, updates"
  - "deployment update, alternative locations"
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Specify an Alternate Location for Deployment Updates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può essere installata inizialmente da un CD o da una condivisione file, ma deve essere configurata in modo da verificare la disponibilità di aggiornamenti periodici sul Web.  È possibile specificare un percorso alternativo per gli aggiornamenti nel manifesto di distribuzione in modo da consentire l'aggiornamento automatico dell'applicazione dal Web dopo l'installazione iniziale.  
  
> [!NOTE]
>  Per l'utilizzo di questa funzionalità, l'applicazione deve essere configurata per l'installazione locale.  Per ulteriori informazioni, vedere [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Inoltre, se si installa l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dalla rete, l'eventuale percorso alternativo impostato verrà utilizzato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sia per l'installazione iniziale sia per tutti gli aggiornamenti successivi.  Se invece si installa l'applicazione localmente, ad esempio da un CD, l'installazione iniziale verrà eseguita dal supporto originale e per tutti gli aggiornamenti successivi verrà utilizzato il percorso alternativo.  
  
### Impostazione di un percorso alternativo per gli aggiornamenti mediante MageUI.exe \(utilità basata su Windows Form\)  
  
1.  Aprire una finestra del prompt dei comandi di .NET Framework e digitare:  
  
     **mageui.exe**  
  
2.  Scegliere **Apri** dal menu **File** per aprire il manifesto di distribuzione dell'applicazione.  
  
3.  Fare clic sulla scheda **Opzioni di distribuzione**.  
  
4.  Nella casella di testo **URL di avvio** immettere l'URL della directory che conterrà il manifesto di distribuzione per gli aggiornamenti dell'applicazione.  
  
5.  Salvare il manifesto di distribuzione.  
  
### Impostazione di un percorso alternativo per gli aggiornamenti mediante Mage.exe  
  
1.  Aprire una finestra del prompt dei comandi di .NET Framework.  
  
2.  Impostare il percorso di aggiornamento utilizzando il seguente comando.  In questo esempio, **HelloWorld.exe.application** è il percorso del manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], che ha sempre l'estensione application, e **http:\/\/adatum.com\/Update\/Path** è l'URL in cui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verificherà la disponibilità di aggiornamenti.  
  
     **Mage \-Update HelloWorld.exe.application \-ProviderUrl http:\/\/adatum.com\/Update\/Path**  
  
3.  Salvare il file.  
  
    > [!NOTE]
    >  A questo punto sarà necessario firmare nuovamente il file mediante Mage.exe.  Per ulteriori informazioni, vedere [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Sicurezza di .NET Framework  
 Se si installa l'applicazione da un supporto offline, ad esempio un CD, e il computer è online, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] controllerà innanzitutto l'URL specificato dal tag `<deploymentProvider>` nel manifesto di distribuzione per determinare se nel percorso di aggiornamento è presente una versione più recente dell'applicazione.  In caso affermativo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installerà l'applicazione direttamente da questo percorso, anziché dalla directory di installazione iniziale, e Common Language Runtime \(CLR\) determinerà il livello di attendibilità dell'applicazione in base a `<deploymentProvider>`.  Se il computer è offline, oppure `<deploymentProvider>` non è raggiungibile, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eseguirà l'installazione dal CD e CLR concederà l'attendibilità in base al punto di installazione. Nel caso di un'installazione da CD, ciò significa che all'applicazione verrà concessa l'attendibilità totale.  Questo livello di attendibilità verrà ereditato da tutti gli aggiornamenti successivi.  
  
 Nel manifesto di tutte le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che utilizzano `<deploymentProvider>` devono essere dichiarate esplicitamente le autorizzazioni necessarie per evitare che vengano assegnati livelli di attendibilità diversi su computer differenti.  
  
## Vedere anche  
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)