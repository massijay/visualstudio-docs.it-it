---
title: "Procedura: eseguire la migrazione di progetti di estendibilit&#224; di Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK, l'aggiornamento"
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Procedura: eseguire la migrazione di progetti di estendibilit&#224; di Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Di seguito viene illustrato come aggiornare l'estensione.  
  
> [!IMPORTANT]
>  Se si prevede di gestire una versione della soluzione di estensione per una versione precedente di Visual Studio, assicurarsi di effettuare una copia prima di aggiornarlo. Potrebbe essere difficile restituire la versione aggiornata allo stato precedente.  
  
#### Per aggiornare una soluzione di estendibilità  
  
1.  Utilizzando la copia si desidera aggiornare, aprirlo nella nuova versione. Verrà richiesto che l'aggiornamento non è reversibile.  
  
2.  Al termine dell'aggiornamento, modificare il percorso del programma esterno per la nuova versione di devenv.exe. Pulsante destro del mouse sul nodo del progetto nel **Esplora**, quindi scegliere **proprietà**. Nel **Debug** scheda, individuare la casella di testo da **Avvia programma esterno** e modificare il percorso di devenv.exe al percorso di Visual Studio 2015, dovrebbe essere simile al seguente:  
  
     **%ProgramFiles%\\Microsoft visual Studio 14.0\\Common7\\IDE\\devenv.exe**  
  
3.  Aggiungere un riferimento a Microsoft.VisualStudio.Shell.14.0.dll. \(Pulsante destro del mouse sul nodo del progetto nel **Esplora** e quindi scegliere **aggiungere \/Reference**. Selezionare il **estensioni** scheda e quindi controllare **Microsoft.VisualStudio.Shell.14.0**.\)  
  
4.  Compilare la soluzione. I file compilati vengono distribuiti per:  
  
     **%LOCALAPPDATA%\\Microsoft\\VisualStudio.14.0Exp\\Extensions\\ \< nome \> \\ \< nome progetto \> \\ \< versione del progetto \> \\**.  
  
#### Per aggiornare un progetto di estensibilità per gli assembly di riferimento NuGet Visual Studio SDK  
  
1.  Determinare gli assembly di riferimento di Visual Studio SDK che richiesto dal progetto.  In **Esplora**, espandere il progetto **riferimenti** nodo ed esaminare l'elenco di riferimenti al progetto.  Assembly di riferimenti di Visual Studio SDK avranno il prefisso **Microsoft.VisualStudio** il nome \(ad esempio: Microsoft.VisualStudio.Shell.14.0\).  
  
2.  Rimuovere gli assembly di riferimento di Visual Studio SDK dal progetto mediante la relativa selezione, fare clic e **rimuovere**.  
  
3.  Aggiungere le versioni NuGet degli assembly di riferimento di Visual Studio SDK.  Mentre ancora il **i riferimenti di Esplora soluzioni** nodo, aprire il **Gestisci pacchetti NuGet** finestra di dialogo.  Se si desidera approfondire la conoscenza di questa finestra di dialogo, vedere [la gestione di pacchetti NuGet mediante la finestra di dialogo](http://docs.nuget.org/Consume/Package-Manager-Dialog). Gli assembly di riferimento di Visual Studio SDK sono stati pubblicati nel [nuget.org](http://www.nuget.org) da [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Utilizzando **nuget.org** come il **origine del pacchetto**, cercare il nome del pacchetto NuGet che corrisponde all'assembly di riferimento desiderato \(ad esempio: Microsoft.VisualStudio.Shell.14.0\) e installarlo nel progetto.  NuGet è possibile aggiungere più assembly di riferimento per soddisfare le dipendenze dell'assembly iniziale.  
  
     Se si preferisce, è possibile aggiungere contemporaneamente tutti gli assembly di riferimento di Visual Studio SDK, installare il SDK di Visual Studio [pacchetto Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  È anche possibile passare a utilizzando la versione NuGet degli strumenti di compilazione di Visual Studio SDK. Questo pacchetto NuGet è [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) e una volta aggiunto per includere gli strumenti necessari e file che consente di compilare il progetto di estensibilità in un computer senza installato il SDK di Visual Studio di destinazione del progetto di.  
  
> [!NOTE]
>  Non è necessario aggiornare i progetti di estendibilità esistenti per l'utilizzo di strumenti e gli assembly di riferimento NuGet.  È possibile continuare a compilare tramite gli assembly di riferimento e gli strumenti installati con il SDK di Visual Studio.