---
title: "Procedura: eseguire il debug di codice inserito | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.injected"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "linguaggio dell'assembly, visualizzazione"
  - "debug [C++], attivazione dell'annotazione del codice sorgente"
  - "debug [C++], codice inserito"
  - "debug [C++], utilizzo di attributi"
  - "debug [C++], visualizzazione di codice assembly"
  - "codice disassembly, debug"
  - "codice inserito"
  - "Mostra codice sorgente (comando) [debugger]"
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: eseguire il debug di codice inserito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere Importa\/Esporta impostazioni dal menu Strumenti.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il ricorso agli attributi può semplificare notevolmente la programmazione in C\+\+.  Per ulteriori informazioni, vedere [Concepts](/visual-cpp/windows/attributed-programming-concepts).  Alcuni attributi sono interpretati direttamente dal compilatore.  Con altri attributi è invece possibile inserire codice nell'origine del programma, il quale verrà quindi compilato dal compilatore.  Questo codice inserito rende più semplice la programmazione perché riduce la quantità di codice che è necessario scrivere.  A volte, tuttavia, può accadere che un bug arresti l'applicazione mentre è in esecuzione il codice inserito.  Quando ciò accade, può essere utile esaminare tale codice  e Visual Studio prevede due metodi per farlo:  
  
-   Visualizzare il codice inserito nella finestra **Disassembly**.  
  
-   Creare, mediante [\/Fx](/visual-cpp/build/reference/fx-merge-injected-code), un file di origine unito contenente il codice originale e il codice inserito.  
  
 Nella finestra **Disassembly** vengono visualizzate le istruzioni in linguaggio assembly che corrispondono al codice sorgente e al codice inserito da attributi.  Nella finestra **Disassembly** sono inoltre riportate le annotazioni del codice sorgente.  
  
### Per attivare l'annotazione del codice sorgente  
  
-   Fare clic con il pulsante destro del mouse sulla finestra **Disassembly** e scegliere **Mostra codice sorgente** dal menu di scelta rapida.  
  
     Se si conosce la posizione di un attributo in una finestra di origine, sarà possibile utilizzare il menu di scelta rapida per trovare il codice inserito nella finestra **Disassembly**.  
  
### Per visualizzare il codice inserito  
  
1.  Il debugger deve essere in modalità di interruzione.  
  
2.  In una finestra di codice sorgente, portare il cursore davanti all'attributo di cui si desidera visualizzare il codice inserito.  
  
3.  Fare clic con il pulsante destro del mouse e scegliere **Vai a disassembly** dal menu di scelta rapida.  
  
     Se l'attributo si trova vicino al punto di esecuzione corrente, sarà possibile scegliere la finestra **Disassembly** dal menu **Debug**.  
  
### Per visualizzare il codice disassembly al punto di esecuzione corrente  
  
1.  Il debugger deve essere in modalità di interruzione.  
  
2.  Scegliere **Finestre** dal menu **Debug** e fare clic su **Disassembly**.  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)