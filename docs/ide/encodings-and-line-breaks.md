---
title: "Codifiche e interruzioni di riga | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.Encoding"
helpviewer_keywords: 
  - "editor, interruzioni di riga"
  - "codifica"
  - "caratteri di interruzione di riga"
  - "interruzioni di riga"
  - "Visual Studio, codifica"
  - "Visual Studio, caratteri di interruzione di riga"
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Codifiche e interruzioni di riga
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual Studio è possibile utilizzare il  **Opzioni di salvataggio di File\/Advanced** le impostazioni per determinare il tipo di interruzione di riga caratteri si desidera.  È inoltre possibile modificare la codifica di un file con le stesse impostazioni.  
  
> [!NOTE]
>  Se si dispongono di determinati tipi di impostazioni di sviluppo \(sviluppo Web, F\#, Visual Basic\) potrebbe non essere visualizzato  **Opzioni di salvataggio avanzate** dal menu.  Per modificare le impostazioni \(ad esempio, in generale\), aprire  **degli strumenti \/ Importa \/ Esporta impostazioni**.  Per ulteriori informazioni, vedere  [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 In Visual Studio i seguenti caratteri vengono interpretati come interruzioni di riga:  
  
-   CRLF: ritorno un capo \+ avanzamento riga, caratteri Unicode 000D \+ 000A  
  
-   LF: avanzamento riga, carattere Unicode 000A  
  
-   NEL: riga successiva, carattere Unicode 0085  
  
-   LS: separatore di riga, carattere Unicode 2028  
  
-   PS: separatore di paragrafo, carattere Unicode 2029  
  
 Testo copiato da altre applicazioni mantiene la codifica originale e i caratteri di interruzione di riga.  Ad esempio, quando si copia testo da blocco note e incollarlo in un file di testo in Visual Studio, il testo presenta le stesse impostazioni che aveva in blocco note.  
  
 Quando si apre un file con caratteri di interruzione di riga diversi, si può vedere una finestra di dialogo che chiede se i caratteri di interruzione di riga incoerenti devono essere normalizzati e il tipo di interruzioni di riga selezionate.