---
title: "Finestra di dialogo Avviso di codice non aggiornato | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.ENC.stalecode"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Avviso di codice non aggiornato (finestra di dialogo)"
  - "codice, avviso di codice non aggiornato"
  - "avvisi, finestra di dialogo Avviso di codice non aggiornato"
  - "Modifica e continuazione, codice non aggiornato"
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Finestra di dialogo Avviso di codice non aggiornato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo viene visualizzata quando si sono apportate modifiche al codice nativo che la modalità **Modifica e continuazione** non può applicare immediatamente.  Di conseguenza, il codice nativo nello stack frame corrente non sarà più aggiornato.  Per ulteriori informazioni, vedere [How to: Work with Stale Code](http://msdn.microsoft.com/it-it/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **Non visualizzare più questo messaggio**  
 Se si seleziona questa casella di controllo, la modalità Modifica e continuazione applicherà le modifiche al codice senza chiedere l'autorizzazione.  Per riattivare questo messaggio di avviso, accedere alla finestra di dialogo **Opzioni**, aprire la cartella **Debug**, fare clic sulla pagina **Modifica e continuazione** e selezionare **Avvisa in caso di codice non aggiornato**.  
  
## Vedere anche  
 [Modifiche e limitazioni del codice supportato \(C\+\+\)](../debugger/supported-code-changes-cpp.md)   
 [Modifica e continuazione, Debug, finestra di dialogo Opzioni](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)