---
title: "Procedura: modificare la directory dell&#39;output compilato | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "directory di output, modifica"
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: modificare la directory dell&#39;output compilato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il percorso dell'output generato dal progetto può essere specificato a livello di singole configurazioni \(per debug e\/o rilascio\).  
  
> [!NOTE]
>  Se si ha un progetto **Installazione**, vedere la nota alla fine di questo articolo.  
  
## Modifica della directory dell'output di compilazione  
  
#### Per modificare la directory dell'output di compilazione  
  
1.  Nella barra dei menu scegliere **Progetto**, *NomeApp***Proprietà**. In alternativa, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**.  
  
2.  Per i progetti Basic, selezionare la scheda **Compilazione**. Per i progetti Visual C\#, selezionare la scheda **Compilazione**. Per un progetto C\+\+ o JavaScript, selezionare la scheda **Generale**.  
  
3.  Nell'elenco a discesa della configurazione nella parte superiore, scegliere la configurazione per cui si vuole modificare il percorso di output \(debug, rilascio o tutte\).  
  
     Individuare la voce relativa al percorso di output \(**Percorso dell'output di compilazione** in Visual Basic **Directory di output** in Visual C\+\+, **Percorso di Output** in JavaScript e C\#\). Specificare una nuova directory dell'output di compilazione relativa alla directory del progetto.  
  
> [!NOTE]
>  In un progetto di installazione, la casella **Nome file di output** modifica solo il percorso del file Setup.exe file, non il percorso dei file di progetto. Per ulteriori informazioni, vedere **Compilazione, proprietà di configurazione, finestra di dialogo delle proprietà del progetto di distribuzione**.  
  
## Vedere anche  
 [Pagina Compilazione, Progettazione progetti \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)   
 [Pagina delle proprietà Generale \(Progetto\)](/visual-cpp/ide/general-property-page-project)   
 [Compilazione di applicazioni in Visual Studio](../ide/compiling-and-building-in-visual-studio.md)