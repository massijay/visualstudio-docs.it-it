---
title: Installare Visual Studio per Mac
description: Istruzioni su come installare Visual Studio per Mac e i componenti aggiuntivi necessari per lo sviluppo multipiattaforma.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 24d2fa5f9054e621cd5167692a2571e9275c2bae
ms.contentlocale: it-it
ms.lasthandoff: 08/11/2017

---

# <a name="setup-and-install-visual-studio-for-mac"></a>Configurare e installare Visual Studio per Mac

## <a name="setup"></a>Configurazione

Per iniziare a sviluppare app native multipiattaforma quando si scarica Visual Studio per Mac, è necessario eseguire alcune operazioni di installazione e configurazione di preparazione.

Per l'uso di iOS in Visual Studio è necessario quanto segue:

* Mac con macOS Sierra 10.12 o versione successiva
* Xcode 8.3
* ID Apple. Se non si ha ancora un ID Apple, è possibile crearne uno nuovo all'indirizzo https://appleid.apple.com. L'ID Apple è necessario per installare Xcode e accedervi.

## <a name="install"></a>Installazione di

1. Scaricare Visual Studio per Mac da [https://www.visualstudio.com/](https://www.visualstudio.com/)

2. Una volta scaricato il pacchetto di installazione, fare clic sul file **VisualStudioInstaller.dmg** per montare il programma di installazione e quindi eseguirlo facendo doppio clic sul logo, come illustrato nell'immagine seguente:

  ![Finestra di dialogo del programma di installazione](media/installer-image1.png)

3. Potrebbe venire visualizzata una finestra di dialogo di avviso simile a quella dell'immagine seguente. In questo caso, fare clic su **Apri**:

  ![Finestra di dialogo di avviso](media/installer-image2.png)

4. Il programma di installazione controlla il sistema per verificare quali componenti devono essere installati o aggiornati:

  ![Valutazione del sistema](media/installer-image3.png)

5. Verrà quindi visualizzata una finestra di dialogo di avviso che chiede di accettare le condizioni di licenza e privacy. Fare clic su **Continua** per accettare le condizioni:

  ![Finestra di dialogo relativa alla licenza](media/installer-image4.png)

6. Il programma di installazione visualizza un elenco dei componenti necessari che non sono presenti e che devono essere scaricati e installati. Selezionare i prodotti da scaricare:

  ![Selezionare gli elementi](media/installer-image5.png)

  Questa schermata di installazione mostra la versione e le dimensioni di ogni singolo componente. È possibile fare clic su ogni componente per visualizzare un elenco delle relative dipendenze (per Android), visualizzare altri pacchetti scaricati (per .NET Core) o visualizzare le applicazioni aggiuntive necessarie (per iOS e macOS):

  ![Dipendenze aggiuntive di Android](media/installer-image6.png)

7. Una volta selezionate le opzioni desiderate, fare clic su **Installa e aggiorna** per avviare il processo di installazione.

8. Il programma di installazione avvia il processo di download e installazione degli elementi selezionati:

  ![Avvio dell'installazione](media/installer-image7.png)

  ![Download di Xamarin.Mac](media/installer-image8.png)

  ![Completamento dell'installazione](media/installer-image9.png)

9. Potrebbe essere necessario elevare le autorizzazioni necessarie per i singoli componenti richiesti per il completamento dell'installazione. Immettere le credenziali di amministratore in questa posizione per continuare il processo di installazione:

  ![Immettere le autorizzazioni per continuare l'installazione](media/installer-image10.png)

10. Una volta completata l'installazione, è possibile iniziare a sviluppare app in Visual Studio premendo **Avvia**:

  ![Aprire Visual Studio](media/installer-image11.png)

> [!NOTE]
Se si sceglie di non installare una piattaforma o uno strumento durante l'installazione originale (deselezionandolo nel passaggio 6), è necessario eseguire di nuovo il [programma di installazione](https://www.visualstudio.com/vs/) se si vuole aggiungere i componenti in un secondo momento.

