---
title: Specifica di eventi di compilazione personalizzati in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e17e8ada438ab8b7223bd9fcaca326c91e69f901
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Specifica di eventi di compilazione personalizzati in Visual Studio
Se si specifica un evento di compilazione personalizzato, sarà possibile eseguire automaticamente i comandi prima dell'avvio o dopo il completamento di una compilazione. Ad esempio, è possibile eseguire un file con estensione bat prima dell'avvio di una compilazione o copiare nuovi file in una cartella dopo il completamento della compilazione. Gli eventi di compilazione vengono eseguiti solo se la compilazione raggiunge correttamente i punti corrispondenti nel processo di compilazione.  
  
 Per informazioni specifiche sul linguaggio di programmazione in uso, vedere gli argomenti seguenti:  
  
-   Visual Basic: [Procedura: specificare gli eventi di compilazione (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).  
  
-   Visual C# e F#: [ Procedura: specificare eventi di compilazione (C#)](../ide/how-to-specify-build-events-csharp.md).  
  
-   Visual C++: [Specifica di eventi di compilazione](/cpp/ide/specifying-build-events).  
  
## <a name="syntax"></a>Sintassi  
 Gli eventi di compilazione seguono la stessa sintassi dei comandi DOS, ma è possibile usare macro per creare con maggiore facilità gli eventi di compilazione. Per un elenco delle macro disponibili, vedere [Finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
 Per ottenere risultati ottimali, seguire questi suggerimenti di formattazione:  
  
-   Aggiungere un'istruzione `call` prima di tutti gli eventi di compilazione che eseguono file con estensione bat.  
  
     Esempio: `call C:\MyFile.bat`  
  
     Esempio: `call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   Racchiudere tra virgolette i percorsi dei file.  
  
     Esempio (per [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"  
  
-   Separare più comandi usando le interruzioni di riga.  
  
-   Includere i caratteri jolly, se necessario.  
  
     Esempio: `for %I in (*.txt *.doc *.html) do copy %I c:\`*directory*`\`  
  
    > [!NOTE]
    >  `%I` nel codice sopra riportato deve essere `%%I` negli script batch.  
  
## <a name="see-also"></a>Vedere anche  
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md)  (Compilazione e creazione)  
 [Finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md)   
 [Procedura dettagliata: compilazione di un'applicazione](../ide/walkthrough-building-an-application.md)