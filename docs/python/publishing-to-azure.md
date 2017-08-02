---
title: Pubblicazione di un&quot;app Python nel servizio app di Azure da Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85031f91-3a65-463b-a678-1e69f1b843e6
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 0163d1279b41ef8fecf9ca774cd3e67f0f47f1b1
ms.lasthandoff: 03/07/2017

---

# <a name="publishing-to-azure-app-service"></a>Pubblicazione nel servizio app di Azure

Per iniziare a creare rapidamente un sito Web Python in Visual Studio e pubblicarlo nel servizio app di Azure, è possibile eseguire la procedura seguente:

- [Creare una sottoscrizione di Azure](#create-an-azure-subscription)
- [Creare e testare il progetto iniziale](#create-and-test-the-initial-project)
- [Eseguire la pubblicazione nel servizio app di Azure](#publish-to-azure-app-service)

Per una breve panoramica di questo processo è possibile guardare il video [Visual Studio Python Tutorial: Building a Website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (Esercitazione su Python in Visual Studio: creazione di un sito Web) su youtube.com (durata: 3minuti e 10 secondi). 

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk] 

## <a name="create-an-azure-subscription"></a>Creare una sottoscrizione di Azure

Per la pubblicazione in Azure è necessaria una sottoscrizione di Azure; in alternativa è possibile usare un sito temporaneo.

Per le sottoscrizioni, iniziare con un [account Azure completo gratuito](https://azure.microsoft.com/en-us/free/), che include un congruo numero di crediti per i servizi di Azure. Valutare anche l'opportunità di iscriversi [Visual Studio Dev Essentials](https://azure.microsoft.com/en-us/pricing/member-offers/vs-dev-essentials/), che include ogni mese 25 dollari di credito per un intero anno.

Per creare un sito temporaneo nel servizio app di Azure senza usare una sottoscrizione di Azure:

1. Aprire il browser e accedere all'indirizzo [try.azurewebsites.net](https://try.azurewebsites.net).
1. Selezionare **App Web** come tipo di applicazione e quindi selezionare **Successivi**.
1. Selezionare **Sito vuoto** come modello e quindi selezionare **Creazione >**.
1. Accedere con un qualsiasi account di accesso di social networking e dopo qualche istante il sito sarà pronto all'URL visualizzato.
1. Selezionare **Scarica profilo di pubblicazione** e salvare il file `.publishsettings`, che verrà usato più tardi.

## <a name="create-and-test-the-initial-project"></a>Creare e testare il progetto iniziale

1. In Visual Studio selezionare **File > Nuovo > Progetto**, cercare "Bottle", selezionare **Progetto Web Bottle** e fare clic su **OK**.    

1. Quando viene richiesto di installare i pacchetti esterni, selezionare **Installa in un ambiente virtuale**. Si noti il controllo **Mostra pacchetti necessari** nella parte inferiore della finestra di dialogo che indica quali pacchetti verranno installati:

  ![Installazione dei pacchetti necessari](~/python/media/tutorials-common-external-packages.png)

1. Selezionare l'interprete di base preferito per l'ambiente virtuale, ad esempio **Python 2.7** o **Python 3.4**, quindi fare clic su **Crea**:

  ![Aggiunta di un ambiente virtuale durante la creazione di un progetto](~/python/media/tutorials-common-add-virtual-environment.png)

1. Al termine, selezionare **Debug > Avvia debug** o premere F5 per testare in locale il progetto creato. Per impostazione predefinita, l'applicazione usa un repository in memoria che non richiede alcuna configurazione. Tutti i dati andranno persi dopo l'arresto del server Web.

1. Fare clic in vari punti dell'applicazione per verificare il funzionamento.

1. Al termine, selezionare **Debug > Arresta debug** o premere MAIUSC+F5 per arrestare il debug.

## <a name="publish-to-azure-app-service"></a>Eseguire la pubblicazione nel servizio app di Azure

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**. 

1. Nella finestra di dialogo **Pubblica** selezionare **Servizio app di Microsoft Azure**:

  ![Passaggio 1 della pubblicazione in Azure](~/python/media/tutorials-common-publish-1.png)

1. Selezionare una destinazione:

    - Se si dispone di una sottoscrizione di Azure, selezionare **Servizio app di Microsoft Azure** come destinazione di pubblicazione e quindi nella finestra di dialogo successiva selezionare un servizio app esistente oppure selezionare **Nuovo** per crearne uno nuovo.
    - Se si usa un sito temporaneo creato su try.azurewebsites.net, selezionare **Importa** come destinazione di pubblicazione, cercare il file `.publishsettings` scaricato dal sito e quindi fare clic su **OK**.

1. I dettagli del servizio app vengono visualizzati nella scheda **Connessione** della finestra di dialogo **Pubblica** seguente.

  ![Passaggio 2 della pubblicazione in Azure](~/python/media/tutorials-common-publish-2.png)

1. Se necessario, selezionare **Avanti >** per esaminare le impostazioni aggiuntive. Se si intende di [eseguire il debug del codice Python in Azure in modalità remota](debugging-azure-remote.md), è necessario impostare **Configurazione** su **Debug**.
1. Selezionare **Pubblica**. Dopo la distribuzione dell'applicazione in Azure, il sito verrà visualizzato nel browser predefinito. 
