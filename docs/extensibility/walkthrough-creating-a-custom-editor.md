---
title: "Procedura dettagliata: Creazione di un Editor personalizzato | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], personalizzato - creazione"
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura dettagliata: Creazione di un Editor personalizzato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il modello di progetto VSPackage è possibile creare un semplice editor personalizzato in C\+\+.  Il modello di progetto VSPackage non supporta più progetti in c\# o Visual Basic. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Il modello di progetto del pacchetto Visual Studio  
 Il modello di progetto Package Visual Studio è reperibile nella **Nuovo progetto** finestra di dialogo nella cartella Extensibility C\+\+  
  
### Per creare un VSPackage utilizzando il modello di pacchetto di Visual Studio  
  
1.  Creare un progetto con il modello di pacchetto di Visual Studio.  
  
2.  Selezionare il **Editor personalizzato** opzione e fare clic su **Avanti**. Il **Opzioni dell'Editor** viene visualizzata la pagina.  
  
3.  Digitare il nome dell'editor nel **nome Editor** casella. Digitare l'estensione del file che si desidera associare con l'editor nel **estensione** casella. L'editor è disponibile per i file con questa estensione. L'estensione del file viene registrato per Visual Studio, non per Windows. Digitare il nome file predefinito per nuovi documenti creati con l'editor nel **Nome File predefinito** casella.  
  
4.  Fare clic su **Fine** per creare il pacchetto VSPackage nella cartella specificata.  
  
### Per testare l'editor personalizzato  
  
1.  Nel **File** dal menu **New** e quindi fare clic su **File**.  
  
2.  Nel **modelli installati** riquadro del **Nuovo File** la finestra di dialogo, selezionare il modello di file, quindi il file di tipo si è appena registrato.  
  
3.  Fare clic su **aprire** per visualizzare e modificare il documento.  
  
     L'editor supporta operazioni di taglia e Incolla, ricerca e sostituzione e open\-and\-load.  
  
## Vedere anche  
 [Package VS](../extensibility/internals/vspackages.md)