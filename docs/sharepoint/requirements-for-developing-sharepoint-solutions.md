---
title: "Requisiti per lo sviluppo di soluzioni SharePoint | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, prerequisiti"
  - "sviluppo per SharePoint in Visual Studio, requisiti"
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Requisiti per lo sviluppo di soluzioni SharePoint
  Prima di poter utilizzare gli strumenti di sviluppo di soluzioni SharePoint inclusi in Visual Studio, è necessario che nel sistema siano stati installati i seguenti prerequisiti:  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] o un'edizione di Visual Studio Application Lifecycle Management \(ALM\).  
  
    -   Funzionalità di [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] o entrambe, quando si installa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installato in [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] a 64 bit o in [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
     oppure  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] installato in [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] a 64 bit o in [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
> [!NOTE]  
>  Nonostante siano supportati ufficialmente da SharePoint solo sistemi operativi server, sono consentiti due sistemi operativi client: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] e [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1.  Per ulteriori informazioni, vedere [Guida all'installazione per workstation di sviluppo di SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkID=164557).  
  
 I tipi di progetto Modello di integrazione applicativa dei dati \(BDC\) richiedono che nel sistema sia stato installato [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)].  
  
 Per sviluppare soluzioni SharePoint in Visual Studio, è necessario installare SharePoint nello stesso computer di Visual Studio.  Inoltre, gli strumenti di sviluppo di SharePoint supportano una sola configurazione autonoma di SharePoint; non supportano una configurazione farm \(remota\).  
  
> [!NOTE]  
>  I progetti SharePoint in Visual Studio supportano solo [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  Se si seleziona [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] per un nuovo progetto SharePoint, esso sarà comunque destinato a [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  
  
 Per ulteriori informazioni sulle modalità di installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vedere [Installazione di Visual Studio](../Topic/Installing%20Visual%20Studio.md).  
  
## Controllo dell'account utente di Vista e Windows 7  
 In [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] è inclusa una funzionalità di sicurezza nota come Controllo dell'account utente \(UAC \- User Account Control\).  Per sviluppare soluzioni SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nei sistemi [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], il controllo dell'account utente richiede l'esecuzione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come amministratore di sistema.  Sul desktop, aprire il menu di scelta rapida per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], quindi scegliere **Esegui come amministratore**.  
  
 Per configurare il collegamento sul desktop in modo da eseguire sempre come amministratore, aprire il menu del collegamento, scegliere **Proprietà**, selezionare il pulsante **Avanzate**, quindi mettere la spunta sulla casella di controllo **Esegui come amministratore**.  
  
 Per ulteriori informazioni, vedere [Informazioni e configurazione di Controllo account utente in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476) e [Controllo dell'account utente di Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Considerazioni sulle autorizzazioni di SharePoint  
 Per sviluppare soluzioni SharePoint, è necessario disporre delle autorizzazioni per eseguire ed effettuare il debug delle soluzioni SharePoint.  Prima di poter testare una soluzione SharePoint, effettuare i passaggi riportati di seguito per assicurarsi di disporre delle autorizzazioni necessarie:  
  
1.  Aggiungere il proprio account utente come amministratore nel sistema.  
  
2.  Aggiungere l'account utente come amministratore farm per il server SharePoint.  
  
    1.  Nell'amministrazione centrale di SharePoint fare clic sul collegamento **Gestisci gruppo amministratori farm**.  
  
    2.  Nella pagina **Amministratori farm**, scegliere il pulsante **Nuovo**.  
  
3.  Aggiungere l'account utente al gruppo WSS\_ADMIN\_WPG.  
  
## Vedere anche  
 [Getting Started &#40;SharePoint Development in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  