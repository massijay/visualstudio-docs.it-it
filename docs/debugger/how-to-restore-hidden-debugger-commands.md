---
title: "Procedura: ripristinare comandi nascosti del debugger | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "comandi, debugger"
  - "debugger, ripristino di comandi"
  - "debug [Visual Studio], ripristino di comandi"
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Procedura: ripristinare comandi nascosti del debugger
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si installa Visual Studio, viene chiesto di scegliere una serie di impostazioni IDE predefinite per il linguaggio di programmazione principale.  Le impostazioni IDE predefinite per alcuni linguaggi possono nascondere determinati comandi del debugger.  
  
 Se si desidera utilizzare una funzionalità del debugger nascosta dalle impostazioni IDE predefinite, è possibile aggiungere di nuovo il comando al menu come descritto nella procedura riportata di seguito.  
  
### Per ripristinare comandi nascosti del debugger  
  
1.  Dopo avere aperto un progetto, scegliere **Personalizza** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Personalizza** fare clic sulla scheda **Comandi**.  
  
3.  Nell'elenco a discesa **Barra dei menu:** selezionare il menu **Debug** in cui si desidera includere il comando ripristinato.  
  
4.  Fare clic sul pulsante **Aggiungi comando**.  
  
5.  Nella casella **Aggiungi comando** selezionare il comando che si desidera aggiungere e fare clic su **OK**.  
  
6.  Ripetere il passaggio precedente per aggiungere un altro comando.  
  
7.  Dopo avere aggiunto tutti i comandi desiderati al menu, fare clic su **Chiudi**.  
  
    > [!WARNING]
    >  Alcune voci di menu vengono visualizzate solo quando nel debugger è attivata una particolare modalità, ad esempio la modalità di esecuzione o la modalità di interruzione.  Le voci aggiunte potrebbero quindi non essere immediatamente visualizzate al termine di questa procedura.  
  
## Ripristino di comandi non disponibili nella finestra di dialogo Personalizza  
 Alcuni comandi, in particolare quelli facenti parte di menu gerarchici, non possono essere ripristinati dalla finestra di dialogo **Personalizza**.  Per ripristinare tali comandi, è necessario importare una nuova raccolta di impostazioni IDE.  
  
#### Per importare nuove impostazioni IDE  
  
1.  Scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  
  
2.  Nella pagina **Importazione\/Esportazione guidata delle impostazioni** selezionare **Importa le impostazioni di ambiente selezionate** e scegliere **Avanti**.  
  
3.  Nella pagina **Salvare le impostazioni correnti** specificare se si desidera salvare le impostazioni personali correnti e quindi scegliere **Avanti**.  
  
4.  Nella pagina **Scegliere una raccolta di impostazioni da importare** scegliere una raccolta di impostazioni di sviluppo contenente i comandi desiderati nella cartella **Impostazioni predefinite**.  In caso di dubbio sulla raccolta da utilizzare, provare a selezionare **Impostazioni generali per lo sviluppo** o **Impostazioni di sviluppo di Visual C\+\+**, che contengono la maggior parte dei comandi del debugger.  
  
5.  Scegliere **Avanti**.  
  
6.  Nella pagina **Scegliere le impostazioni da importare** assicurarsi che sia selezionata l'opzione **Debug** in **Opzioni**.  Deselezionare le altre caselle di controllo, a meno che non si desideri importare anche tali impostazioni.  
  
7.  Scegliere **Fine**.  
  
8.  Nella pagina **Importazione completa** esaminare gli eventuali errori associati alla riconfigurazione delle impostazioni in **Dettagli**.  
  
9. Fare clic su **Chiudi**.  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)