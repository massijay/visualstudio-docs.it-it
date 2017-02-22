---
title: "Procedura: uscire da codice gestito quando nella finestra Stack di chiamate non sono visualizzati frame nativi | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Finestra Stack di chiamate, frame nativi mancanti"
  - "codice, codice gestito"
  - "frame nativi"
  - "uscita, codice gestito"
  - "codice gestito, uscita"
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: uscire da codice gestito quando nella finestra Stack di chiamate non sono visualizzati frame nativi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se il codice contiene frame nativi non visibili nella finestra **Stack di chiamate**, l'uscita dal codice gestito può produrre risultati imprevisti.  Una soluzione possibile consiste nell'utilizzare un punto di interruzione invece del comando **Esci da istruzione\/routine**.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per uscire da codice gestito quando nella visualizzazione dello stack di chiamate non sono visualizzati frame nativi  
  
1.  Nel codice nativo impostare un punto di interruzione di posizione dopo la chiamata a codice gestito.  
  
2.  Scegliere **Continua** dal menu **Debug**.  
  
     Una volta completata la chiamata gestita, l'esecuzione si interromperà in corrispondenza del punto di interruzione nel codice nativo.  
  
## Vedere anche  
 [Procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md)