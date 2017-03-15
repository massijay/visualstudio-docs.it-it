---
title: "Libreria di controlli Web (Codice gestito) | Microsoft Docs"
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
  - "debug [Visual Studio], librerie di controlli Web"
  - "debug di DLL"
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# Libreria di controlli Web (Codice gestito)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il modello di progetto Libreria di controlli Web consente di creare una DLL.  Poiché la libreria di classi è una DLL, non è possibile eseguirla direttamente.  È necessario creare una pagina di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in cui sia incorporato il controllo.  Per ulteriori informazioni, vedere [Web Control Library Template](http://msdn.microsoft.com/it-it/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### Per eseguire il debug di una libreria di controlli Web \(procedura 1\)  
  
1.  Aprire un progetto Libreria di controlli Web esistente o crearne uno nuovo.  
  
2.  Creare una pagina di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in cui sia incorporato il controllo.  
  
3.  Nel sito Web che ospita il test harness di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] creare una sottodirectory denominata `/Code`.  
  
4.  Copiare il codice sorgente del controllo nella sottodirectory `/Code`.  
  
5.  Aprire il codice sorgente nella sottodirectory `/Code` e impostare i punti di interruzione.  
  
6.  Aprire una finestra del browser con un URL che punta al test harness.  Quando verrà raggiunto un punto di interruzione nel controllo sarà possibile iniziare il debug.  
  
### Per eseguire il debug di una libreria di controlli Web \(procedura 2\)  
  
1.  Creare il progetto dell'applicazione host e il progetto del controllo Web nella stessa soluzione.  
  
2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sull'applicazione host e scegliere **Aggiungi riferimento**.  
  
3.  Aggiungere un riferimento al progetto del controllo Web.  
  
## Vedere anche  
 [Applicazioni Web ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)