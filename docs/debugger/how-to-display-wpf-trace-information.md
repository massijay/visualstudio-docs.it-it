---
title: "Procedura: visualizzare le informazioni di traccia WPF | Microsoft Docs"
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
helpviewer_keywords: 
  - "debug, WPF"
  - "WPF, debug"
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Procedura: visualizzare le informazioni di traccia WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] è in grado di ricevere informazioni di traccia di debug da applicazioni WPF e di visualizzare tali informazioni nella finestra **Output**.  Per visualizzare le informazioni di traccia di debug, la tracciatura WPF deve essere abilitata.  
  
 È possibile abilitare la tracciatura WPF nel file App.Config o a livello di codice utilizzando la classe <xref:System.Diagnostics.PresentationTraceSources>.  Un modo più semplice per abilitare la tracciatura WPF è quello di utilizzare la finestra **Opzioni**.  La tracciatura WPF per applicazioni Web non è supportata.  
  
### Per abilitare o personalizzare le informazioni di traccia WPF  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** aprire il nodo **Debug** nella casella sulla sinistra.  
  
3.  In **Debug** fare clic su **Finestra di output**.  
  
4.  In **Impostazioni generali di output** selezionare **Tutto l'output di debug**.  
  
5.  Nella casella sulla destra ricercare **Impostazioni di traccia WPF**.  
  
6.  Aprire il nodo **Impostazioni di traccia WPF**.  
  
7.  In **Impostazioni di traccia WPF** fare clic sulla categoria di impostazioni che si desidera abilitare, ad esempio **Associazione dati**.  
  
     Verrà visualizzato un controllo elenco a discesa nella colonna Impostazioni accanto ad **Associazione dati** o qualsiasi categoria selezionata.  
  
8.  Fare clic sull'elenco a discesa e selezionare il tipo di informazioni di traccia che si desidera visualizzare: **Tutto**, **Critico**, **Errore**, **Avviso**, **Informazioni**, **Dettaglio** o **Attività**.  
  
     **Critico** abilita solo la tracciatura di eventi Critico.  
  
     **Errore** abilita la tracciatura di eventi Critico ed Errore.  
  
     **Avviso** abilita la tracciatura di eventi Critico, Errore e Avviso.  
  
     **Informazioni** abilita la tracciatura di eventi Critico, Errore, Avviso e Informazioni.  
  
     **Dettaglio** abilita la tracciatura di eventi Critico, Errore, Avviso, Informazione e Dettaglio.  
  
     **Attività** abilita la tracciatura di eventi Interrompi, Avvia, Sospendi, Trasferisci e Riprendi.  
  
     Per ulteriori informazioni sul significato di questi livelli di informazioni di traccia, vedere <xref:System.Diagnostics.SourceLevels>.  
  
9. Scegliere **OK**.  
  
### Per disabilitare le informazioni di traccia WPF  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** aprire il nodo **Debug** nella casella sulla sinistra.  
  
3.  In **Debug** fare clic su **Finestra di output**.  
  
4.  Nella casella sulla destra ricercare **Impostazioni di traccia WPF**.  
  
5.  Aprire il nodo **Impostazioni di traccia WPF**.  
  
6.  In **Impostazioni di traccia WPF** fare clic sulla categoria di impostazioni che si desidera abilitare, ad esempio **Associazione dati**.  
  
     Verrà visualizzato un controllo elenco a discesa nella colonna Impostazioni accanto ad **Associazione dati** o qualsiasi categoria selezionata.  
  
7.  Fare clic sull'elenco a discesa e selezionare **Disattivato**.  
  
8.  Scegliere **OK**.  
  
## Vedere anche  
 [Debug di WPF](../debugger/debugging-wpf.md)