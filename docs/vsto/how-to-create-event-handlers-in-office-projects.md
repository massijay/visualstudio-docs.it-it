---
title: "Procedura: creare gestori eventi in progetti di Office"
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
helpviewer_keywords: 
  - "gestori eventi [sviluppo per Office in Visual Studio]"
  - "eventi [sviluppo per Office in Visual Studio]"
  - "Visual Basic [sviluppo per Office in Visual Studio], gestori eventi"
  - "Visual C# [sviluppo per Office in Visual Studio], gestori eventi"
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Procedura: creare gestori eventi in progetti di Office
  Esistono diversi metodi per creare gestori eventi in Visual Basic e in Visual C\#.  Nella visualizzazione Progettazione, è possibile creare i gestori eventi predefiniti per i controlli facendo doppio clic sul controllo o utilizzare il riquadro degli eventi della finestra **Proprietà** per creare gestori per qualsiasi evento presente nel controllo.  Se si utilizza la visualizzazione Codice, tuttavia, non è necessario passare alla visualizzazione Progettazione per creare un gestore eventi.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Per creare un gestore eventi in Visual Basic  
  
1.  Selezionare l'oggetto per cui si desidera creare un gestore eventi dall'elenco a discesa **Nome classe** nella parte superiore dell'Editor di codice.  
  
    > [!NOTE]  
    >  Se si desidera creare gestori eventi per `ThisDocument` o `ThisWorkbook`, è necessario selezionare **\(ThisDocument Events\)** o **\(ThisWorkbook Events\)** nell'elenco a discesa **Nome classe**  
  
2.  Selezionare l'evento dall'elenco a discesa **Nome metodo** nella parte superiore dell'Editor di codice.  
  
     Visual Studio crea il gestore eventi e sposta il punto di inserimento sul gestore eventi appena creato.  Se il gestore eventi è già presente, il punto di inserimento viene spostato su questo gestore eventi.  
  
### Per creare un gestore eventi in Visual C\#  
  
1.  Creare il delegato dell'evento nell'evento **Startup** della classe digitando il nome completo dell'evento seguito da uno spazio, quindi digitando \+\= senza spazi finali.  Ad esempio:  
  
     `this.<object name>.<event name> +=`  
  
2.  Alla fine del codice, premere il tasto TAB due volte.  
  
     Visual Studio completa automaticamente la riga di codice, crea il gestore eventi e sposta il punto di inserimento sul gestore eventi appena creato.  
  
## Vedere anche  
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Procedura dettagliata: programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)  
  
  