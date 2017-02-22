---
title: "Procedura: creare e modificare le configurazioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurazioni di compilazione, creazione"
  - "configurazioni di compilazione, modifica"
  - "compilazioni [Visual Studio], configurazione"
  - "Gestione configurazione"
  - "configurazioni di compilazione progetti, creazione"
  - "configurazioni di compilazione progetti, modifica"
  - "proprietà (pagine)"
  - "configurazioni di compilazione soluzioni, creazione"
  - "configurazioni di compilazione soluzioni, modifica"
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: creare e modificare le configurazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile creare diverse configurazioni di compilazione per le soluzioni.  Ad esempio, è possibile configurare una compilazione di debug che i tester possono utilizzare per trovare e correggere problemi, ed è possibile configurare diversi tipi di compilazioni che è possibile distribuire a diversi clienti.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Creazione delle configurazioni della compilazione  
 È possibile utilizzare la finestra di dialogo **Gestione configurazione** per selezionare o modificare le configurazioni delle compilazioni esistenti, oppure crearne di nuove.  
  
#### Per aprire la finestra di dialogo Gestione configurazione  
  
-   In **Esplora soluzioni** aprire il menu di scelta rapida per la soluzione e sceglielere **Gestione configurazione**.  
  
    > [!NOTE]
    >  Se il comando **Gestione configurazione** non viene visualizzato nel menu di scelta rapida, cercare il menu **Compilazione** nella barra dei menu.  Se entrambi non vengono visualizzati, dalla barra dei menu, scegliere **Strumenti**, **Opzioni** quindi nel riquadro sinistro della finestra di dialogo **Opzioni**, espandere **Progetti e soluzioni**, **Generale** e nel riquadro di destra, selezionare la casella di controllo **Mostra configurazioni di compilazione avanzate**.  
  
     Nella finestra di dialogo **Gestione configurazione**, è possibile utilizzare l'elenco a cascata **Configurazione soluzione attiva** per selezionare una configurazione di compilazione, modificarne una esistente, o per crearne una nuova..  È possibile utilizzare l'elenco a cascata **Piattaforma soluzione attiva** per selezionare la piattaforma destinazione della configurazione, modificarne una esistente, oppure aggiungerne una nuova.  Nel riquadro **Contesti di progetto** vengono elencati i progetti nella soluzione.  Per ogni progetto, è possibile selezionare una configurazione e una piattaforma specifica per il progetto, modificarne una esistente o crearne una nuova.  È inoltre possibile selezionare caselle di controllo che indicano se ogni progetto viene incluso quando si utilizza la configurazione di compilazione per la soluzione o si distribuisce la soluzione.  
  
 Dopo avere installato le configurazioni desiderate, è possibile impostare le proprietà di progetto appropriate per queste configurazioni.  
  
#### Per impostare le proprietà sulla base delle configurazioni  
  
-   In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto, quindi scegliere **Proprietà**.  
  
     Verrà visualizzata la finestra di dialogo  **Pagine delle proprietà**.  
  
     È possibile impostare delle proprietà per le configurazioni.  Ad esempio, per una configurazione di rilascio, è possibile specificare che il codice deve essere ottimizzato quando si effettua la compilazione della soluzione, e per una configurazione di debug, specificare che il simbolo di compilazione condizionale `DEBUG` deve essere incluso.  Per ulteriori informazioni sulle impostazioni della pagina delle proprietà, vedere [Introduction to the Project Designer](http://msdn.microsoft.com/it-it/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
## Creazione e modifica di una configurazione di progetto  
  
#### Per creare una configurazione di progetto  
  
1.  Aprire la finestra di dialogo **Gestione configurazione**.  
  
2.  Selezionare un progetto nella colonna **Progetto**.  
  
3.  Dalla casella di riepilogo **Configurazione** relativa al progetto, selezionare **Nuovo**.  
  
     Verrà visualizzata la finestra di dialogo **Nuova configurazione progetto**.  
  
4.  Digitare un nome per la nuova configurazione nella casella **Nome**.  
  
5.  Per utilizzare le impostazioni di proprietà specificate da una configurazione di progetto esistente, selezionare una configurazione dalla casella di riepilogo **Copia impostazioni da**.  
  
6.  Per creare contemporaneamente una configurazione di soluzione, selezionare la casella di controllo **Crea nuove configurazioni soluzione**.  
  
#### Per rinominare una configurazione di progetto  
  
1.  Aprire la finestra di dialogo **Gestione configurazione**.  
  
2.  Nella colonna **Progetto**, selezionare il progetto che contiene la configurazione di progetto che si desidera rinominare.  
  
3.  Dalla casella di riepilogo **Configurazione** relativa al progetto, selezionare **Modifica**.  
  
     Verrà visualizzata la finestra di dialogo **Modifica configurazioni progetto**.  
  
4.  Selezionare il nome della configurazione di progetto che si desidera modificare.  
  
5.  Selezionare **Rinomina** e inserire un nuovo nome.  
  
## Creare e modificare configurazioni di compilazione per la soluzione  
  
#### Per creare una configurazione di compilazione della soluzione  
  
1.  Aprire la finestra di dialogo **Gestione configurazione**.  
  
2.  Selezionare **Nuova** dalla casella di riepilogo a cascata **Configurazione soluzione attiva**.  
  
     Verrà visualizzata la finestra di dialogo **Nuova configurazione soluzione**.  
  
3.  Nella casella di testo **Nome** inserire il nome della nuova configurazione.  
  
4.  Per utilizzare le impostazioni specificate da una configurazione esistente, selezionare una configurazione dalla casella di riepilogo **Copia impostazioni da**.  
  
5.  Se si desidera creare configurazioni di progetto contemporaneamente, selezionare la casella di controllo **Crea nuove configurazioni progetto**.  
  
#### Per rinominare una configurazione della build della soluzione  
  
1.  Aprire la finestra di dialogo **Gestione configurazione**.  
  
2.  Selezionare **Modifica** dalla casella di riepilogo a discesa **Configurazione soluzione attiva**.  
  
     Verrà visualizzata la finestra di dialogo **Modifica configurazioni soluzione**.  
  
3.  Selezionare il nome della configurazione della soluzione che si desidera cambiare.  
  
4.  Selezionare **Rinomina** e inserire un nuovo nome.  
  
#### Per modificare una configurazione di compilazione della soluzione  
  
1.  Aprire la finestra di dialogo **Gestione configurazione**.  
  
2.  Nell'elenco a discesa **Configurazione soluzione attiva**, selezionare la configurazione desiderata.  
  
3.  Nel riquadro **Contesti di progetto**, per ogni progetto, selezionare la **Configurazione** e la **Piattaforma** desiderata e scegliere se effettuare la **Compilazione** e se effettuare la **Distribuzione**.  
  
## Vedere anche  
 [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md)   
 [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Procedura: modificare le proprietà e le impostazioni di configurazione dei progetti](http://msdn.microsoft.com/it-it/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)