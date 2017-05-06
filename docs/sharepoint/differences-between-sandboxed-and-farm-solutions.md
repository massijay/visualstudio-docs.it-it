---
title: "Differenze tra soluzioni create mediante sandbox e soluzioni farm"
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
  - "soluzioni farm [sviluppo per SharePoint in Visual Studio]"
  - "soluzioni create mediante sandbox [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, soluzioni farm"
  - "sviluppo per SharePoint in Visual Studio, soluzioni create mediante sandbox"
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Differenze tra soluzioni create mediante sandbox e soluzioni farm
  Quando si compila una soluzione SharePoint, questa viene distribuita nel server SharePoint e ne viene eseguito il debug tramite un debugger che viene connesso alla soluzione.  Il processo utilizzato per eseguire il debug della soluzione dipende dall'impostazione della proprietà Soluzione creata mediante sandbox: soluzione creata mediante sandbox o soluzione farm.  
  
 Per ulteriori informazioni, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
## Soluzioni farm  
 Le soluzioni farm, ospitate nel processo di lavoro IIS \(W3WP.exe\), eseguono codice che può influire sull'intera farm.  Quando si esegue il debug di un progetto SharePoint la cui proprietà Soluzione creata mediante sandbox è impostata su "soluzione farm", il pool di applicazioni IIS del sistema viene riciclato prima che SharePoint ritragga o distribuisca la funzionalità in modo da rilasciare qualsiasi file bloccato dal processo di lavoro IIS.  Solo il pool di applicazioni IIS che serve l'URL del sito del progetto SharePoint viene riciclato.  
  
## Soluzioni create mediante sandbox  
 Le soluzioni create mediante sandbox, ospitate nel processo di lavoro della soluzione del codice utente di SharePoint \(SPUCWorkerProcess.exe\), esegue codice che può influire soltanto sulla raccolta di siti della soluzione.  Poiché le soluzioni create mediante sandbox non vengono eseguite nel processo di lavoro IIS, non occorre riavviare né il pool di applicazioni IIS né il server IIS.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] connette il debugger al processo SPUCWorkerProcess attivato e controllato automaticamente dal servizio SPUserCodeV4 in SharePoint.  Non è necessario che il processo SPUCWorkerProcess esegua il riciclo per caricare la versione più recente della soluzione.  
  
## Entrambi i tipi di soluzione  
 Con entrambi i tipi di soluzione, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] connette il debugger anche al browser per abilitare il debug degli script sul lato client.  A tale scopo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizza il motore di debug degli script.  Per abilitare il debug degli script è necessario modificare le impostazioni del browser predefinite quando viene richiesto.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] connette il debugger solo ai processi W3WP o SPUCWorkerProcess che eseguono il sito corrente.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] connette anche i motori di debug dei componenti gestiti COM Plus e del flusso di lavoro.  
  
## Vedere anche  
 [Debug di soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md)  
  
  