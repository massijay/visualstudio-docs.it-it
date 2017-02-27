---
title: "Procedura: individuare la DLL che ha causato l&#39;arresto anomalo del programma | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, arresti anomali di DLL"
  - "debug [Visual Studio], arresti anomali di DLL"
  - "DLL, ordine di caricamento"
  - "errori [debugger], arresti anomali di DLL"
  - "Module List (finestra di dialogo)"
  - "finestra Moduli"
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: individuare la DLL che ha causato l&#39;arresto anomalo del programma
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere Importa\/Esporta impostazioni dal menu Strumenti.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se l'applicazione si arresta in modo anomalo durante la chiamata a una DLL di sistema o al codice di un altro utente, è necessario identificare la DLL attiva al momento dell'arresto.  Se si verifica un arresto anomalo in una DLL esterna al programma, è possibile identificarne la posizione utilizzando la finestra **Moduli**.  
  
### Per stabilire la posizione in cui si è verificato un arresto anomalo mediante la finestra Moduli  
  
1.  Annotare l'indirizzo in cui si è verificato l'arresto.  
  
2.  Scegliere **Finestre** dal menu **Debug**, quindi **Moduli**.  
  
3.  Nella finestra **Moduli** individuare la colonna **Indirizzo**.  Per visualizzarla potrebbe essere necessario utilizzare la barra di scorrimento.  
  
4.  Fare clic sul pulsante **Indirizzo** nella parte superiore della colonna per ordinare le DLL in base all'indirizzo.  
  
5.  Cercare nell'elenco ordinato la DLL il cui intervallo di indirizzi contenga la posizione in cui si è verificato l'arresto anomalo.  
  
6.  Nelle colonne **Nome** e **Percorso** cercare il nome e il percorso della DLL.  
  
## Vedere anche  
 [Procedura: eseguire il debug di DLL native](../debugger/how-to-debug-native-dlls.md)   
 [Procedura: utilizzare la finestra Moduli](../debugger/how-to-use-the-modules-window.md)