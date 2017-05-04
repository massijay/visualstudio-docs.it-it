---
title: "Tastiera di Microsoft Office Excel, impostazioni della tastiera di Microsoft Office, finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ExcelOptions.KeyboardMappingScheme"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "tasti di scelta rapida, sviluppo per Office in Visual Studio"
ms.assetid: 2a8b9e70-66fa-4461-8039-b6d8a2fbb963
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Tastiera di Microsoft Office Excel, impostazioni della tastiera di Microsoft Office, finestra di dialogo Opzioni
  Sia Microsoft Office Excel che Visual Studio consentono l'utilizzo di tasti di scelta rapida.  La stessa combinazione di tasti di scelta rapida può attivare comandi diversi in Excel e in Visual Studio.  Quando Excel viene aperto in un progetto a livello di documento in Visual Studio, i comandi dei tasti di scelta rapida sono ricevuti da un'applicazione alla volta.  Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è possibile fare in modo che vengano ricevuti da Excel quando il documento ha lo stato attivo selezionando **Schema della tastiera dinamico**.  
  
 Se si utilizza un tasto di scelta rapida che non è assegnato a un comando nell'applicazione che al momento gestisce i tasti di scelta rapida, tale tasto di scelta rapida viene passato all'altra applicazione.  
  
 L'opzione selezionata rimarrà attiva per i progetti Excel fino a quando non la si cambia.  La selezione non ha effetto sui progetti di Microsoft Office Word. Per apportare eventuali modifiche in Word è necessario utilizzare le opzioni della tastiera di Microsoft Office Word.  
  
## Elenco UIElement  
 **Schema della tastiera di Visual Studio**  
 Visual Studio riceve tutti i comandi dei tasti di scelta rapida, anche se Excel ha lo stato attivo.  Se ad esempio si preme il tasto funzione F5 mentre Excel ha lo stato attivo, Visual Studio inizia il debug della soluzione.  
  
 **Schema della tastiera dinamico**  
 Visual Studio riceve i comandi dei tasti di scelta rapida solo quando ha lo stato attivo.  Quando Excel ha lo stato attivo, riceve tutti i comandi dei tasti di scelta rapida.  Se ad esempio si preme il tasto funzione F5 quando Excel ha lo stato attivo, viene aperta la finestra di dialogo **Vai a** di Excel.  Se si preme F5 quando Visual Studio ha lo stato attivo, viene avviato il debug della soluzione.  
  
## Vedere anche  
 [Tastiera di Microsoft Office Word, impostazioni della tastiera di Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  