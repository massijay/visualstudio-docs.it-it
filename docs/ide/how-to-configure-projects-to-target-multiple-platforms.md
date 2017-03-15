---
title: "Procedura: configurare progetti per piattaforme di destinazione multiple | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "piattaforme, modifica delle piattaforme di destinazione"
  - "progetti [Visual Studio], piattaforme di destinazione"
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Procedura: configurare progetti per piattaforme di destinazione multiple
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di destinare una soluzione a più architetture o piattaforme della CPU contemporaneamente.  Le proprietà per impostare questi si accede mediante la finestra di dialogo di **Gestione configurazione** .  
  
## Individuazione della piattaforma di destinazione  
 La finestra di dialogo **Gestione configurazione** consente di creare e impostare configurazioni e piattaforme a livello di soluzione e a livello di progetto.  A ciascuna combinazione di configurazioni e destinazioni a livello di soluzione può essere associato un set di proprietà specifiche, che consentono ad esempio di passare con facilità da una configurazione di rilascio destinata a una piattaforma [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] a una configurazione di rilascio destinata a una piattaforma x86 e a una configurazione di debug destinata una piattaforma x86.  
  
#### Per impostare una configurazione per una piattaforma di destinazione differente  
  
1.  Scegliere **Gestione configurazione** dal menu **Compila**.  
  
2.  Nella casella **Piattaforma soluzione attiva** selezionare la piattaforma a cui si desidera che la soluzione sia destinata oppure selezionare **\<Nuova\>** per creare una nuova piattaforma.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compilerà l'applicazione individuare la piattaforma che viene impostata come piattaforma attiva nella finestra di dialogo di **Gestione configurazione** .  
  
## Rimozione di una piattaforma  
 Se una piattaforma non è necessaria, è possibile rimuoverla utilizzando la finestra di dialogo Gestione configurazione.  Tutte le impostazioni di soluzione e di progetto configurate per tale combinazione di configurazione e destinazione verranno rimosse.  
  
#### Per rimuovere una piattaforma  
  
1.  Scegliere **Gestione configurazione** dal menu **Compila**.  
  
2.  Nella casella **Piattaforma soluzione attiva** selezionare **\<Modifica\>**.  Viene aperta la finestra di dialogo **Modifica piattaforme soluzione**.  
  
3.  Selezionare la piattaforma che si desidera rimuovere e fare clic su **Rimuovi**.  
  
## Destinare una soluzione a più piattaforme  
 Poiché è possibile modificare le impostazioni in base alla combinazione di impostazioni di configurazione e di piattaforma, è possibile destinare una soluzione a più piattaforme.  
  
#### Per destinare una soluzione a più piattaforme  
  
1.  Utilizzare **Gestione configurazione** per aggiungere almeno due piattaforme di destinazione per la soluzione.  
  
2.  Selezionare la piattaforma di destinazione dall'elenco a discesa **Piattaforma soluzione attiva**.  
  
3.  Compilare la soluzione.  
  
#### Per compilare più configurazioni di soluzioni contemporaneamente  
  
1.  Utilizzare **Gestione configurazione** per aggiungere almeno due piattaforme di destinazione per la soluzione.  
  
2.  Utilizzare la finestra **Compilazione batch** per compilare più configurazioni di soluzioni contemporaneamente.  
  
 È possibile che una piattaforma a livello di soluzione sia impostata, ad esempio, su [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] e che i progetti contenuti nella soluzione non siano destinati alla stessa piattaforma.  Inoltre è possibile che la soluzione includa più progetti, ciascuno destinato a piattaforme differenti.  Nel caso si verifichi una di queste situazioni, si consiglia di creare una nuova configurazione con un nome descrittivo per evitare confusione.  
  
## Vedere anche  
 [Procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)   
 [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)   
 [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)