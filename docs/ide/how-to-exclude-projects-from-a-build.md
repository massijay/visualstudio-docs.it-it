---
title: "Procedura: escludere progetti da una compilazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Procedura: escludere progetti da una compilazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile compilare una soluzione senza compilare tutti i progetti contenuti al suo interno.  Ad esempio, si può escludere un progetto che causa l'interruzione della compilazione.  Sarà possibile compilare il progetto in seguito, dopo avere esaminato e risolto i problemi.  
  
 Per escludere un progetto è possibile procedere in due modi:  
  
-   Rimuoverlo temporaneamente dalla configurazione della soluzione attiva.  
  
-   Creare di una configurazione di soluzione che non include il progetto.  
  
 Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
### Per rimuovere temporaneamente un progetto dalla configurazione della soluzione attiva.  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Gestione configurazione**.  
  
2.  Nella tabella **Contesti progetto** individuare il progetto da escludere dalla compilazione.  
  
3.  Nella colonna **Compila** del progetto deselezionare la casella di controllo.  
  
4.  Fare clic sul pulsante **Chiudi**, quindi ricompilare la soluzione.  
  
### Per creare una configurazione di soluzione che esclude un progetto  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Gestione configurazione**.  
  
2.  Nell'elenco **Configurazione soluzione attiva**, scegliere **\<Nuovo\>**.  
  
3.  Nella casella **Nome** immettere un nome per la configurazione di soluzione.  
  
4.  Nell'elenco **Copia impostazioni da** scegliere la configurazione di soluzione su cui si vuole basare la nuova configurazione \(ad esempio **Debug**\), quindi scegliere il pulsante **OK**.  
  
5.  Nella finestra di dialogo **Gestione configurazione** deselezionare la casella di controllo **Compila** per il progetto da escludere e quindi fare clic sul pulsante **Chiudi**.  
  
6.  Nella finestra degli strumenti **Standard** verificare che la nuova configurazione di soluzione sia la configurazione attiva nella casella **Configurazioni soluzione**.  
  
7.  Sulla barra dei menu scegliere **Compilazione**, **Ricompila soluzione**.  
  
## Vedere anche  
 [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)   
 [Procedura: creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)   
 [Procedura: compilare più configurazioni contemporaneamente](../ide/how-to-build-multiple-configurations-simultaneously.md)