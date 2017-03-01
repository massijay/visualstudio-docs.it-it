---
title: 'Procedura dettagliata: Pubblicazione di un&quot;estensione di Visual Studio | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 574af4ff2b3858201c13121475de02a763572f6b
ms.openlocfilehash: fcfb0724b89d60553d6686a0705ab1e9459014ce
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio
Questa procedura dettagliata viene illustrato come pubblicare un'estensione di Visual Studio in Visual Studio Gallery. Quando si aggiunge l'estensione alla raccolta, gli sviluppatori possono utilizzare **estensioni e aggiornamenti** per cercare estensioni nuove e aggiornate.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual Studio  
 In questo caso si userà un'estensione VSPackage predefinito, ma gli stessi passaggi sono validi per ogni tipo di estensione.  
  
1.  Creare un VSPackage in c# denominata `TestPublishing` che dispone di un comando di menu. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="test-the-extension"></a>Testare l'estensione  
 Prima di distribuire l'estensione, creare e testarlo per assicurarsi che sia installato correttamente nell'istanza sperimentale di Visual Studio.  
  
1.  In Visual Studio, avviare il debug. Per aprire un'istanza sperimentale di Visual Studio.  
  
2.  Nell'istanza sperimentale, passare al **strumenti** menu e fare clic su **Gestione estensioni**. L'estensione TestPublishing dovrebbe essere visualizzato nel riquadro centrale e attivata.  
  
3.  Nel **strumenti** menu, assicurarsi che il comando di test è disponibile.  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Pubblicare l'estensione di Visual Studio Gallery  
 È ora possibile pubblicare l'estensione per Visual Studio Gallery.  
  
1.  Assicurarsi di avere creato la versione dell'estensione e che sia aggiornato.  
  
2.  In un Web browser aprire il sito Web [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329) .  
  
3.  Nell'angolo superiore destro, fare clic su **SIGN IN**.  
  
4.  Usare l'account Microsoft per accedere. Se non hai un account Microsoft, è possibile crearne uno a questo punto.  
  
5.  Fare clic su **Upload**.  
  
6.  In **passaggio 1: tipo di estensione**selezionare **strumento** e quindi fare clic su **Avanti**.  
  
7.  In **passaggio 2: caricare**, è possibile scegliere di caricare direttamente in Visual Studio Gallery o aggiungere un collegamento al proprio sito Web. In questo caso selezionare **desidero caricare lo strumento**. Il **selezionare il controllo** viene visualizzata. Fare clic su **Sfoglia** e quindi selezionare TestPublish.vsix nella cartella \bin\release. del progetto. Scegliere **Avanti**.  
  
8.  In **passaggio 3: informazioni di base**, vengono visualizzati i campi del file source.extension.vsixmanifest. Selezionare un'opzione appropriata **categoria** e aggiungere **tag** per consentire agli utenti di trovare l'estensione. Si desideri aggiungere un riepilogo e una descrizione (la descrizione deve essere almeno 280 caratteri) più dettagliate. Lasciare **tipo di estensione** come **non un'estensione Microsoft** e **categoria di costi** come **versione di valutazione**.  
  
9. Leggi l'accordo di contributo nella parte inferiore della pagina **accetto**.  
  
10. Fare clic su **crea contributo**. Verrà visualizzata la pagina che avrà l'estensione in Visual Studio Gallery, con un messaggio che la pagina non è stata pubblicata.  
  
11. Fare clic su **Pubblica**.  
  
12. Raccolta di Visual Studio per l'estensione di ricerca. Dovrebbe essere visualizzato l'elenco per l'estensione TestPublish.  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Installare l'estensione di Visual Studio Gallery  
 Ora che l'estensione viene pubblicato, installarlo in Visual Studio e testarlo.  
  
1.  In Visual Studio, nel **strumenti** menu, fare clic su **estensioni e aggiornamenti**.  
  
2.  Fare clic su **Online** e quindi cercare TestPublish. Dovrebbe essere visualizzato l'elenco per l'estensione TestPublish.  
  
3.  Scegliere **Download**. Dopo aver scaricato l'estensione, fare clic su **Installa**.  
  
4.  Per completare l'installazione, riavviare Visual Studio.  
  
## <a name="removing-the-extension"></a>Rimuovere l'estensione  
 È possibile rimuovere l'estensione di Visual Studio Gallery e dal computer.  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Per rimuovere l'estensione di Visual Studio Gallery  
  
1.  Aprire il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329) sito Web.  
  
2.  Nell'area, fare clic su **estensioni My**. Viene visualizzato l'elenco per TestPublish.  
  
3.  Fare clic su **eliminare**.  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer  
  
1.  In Visual Studio scegliere **Gestione estensioni** dal menu **Strumenti**.  
  
2.  Selezionare TestPublish e quindi fare clic su **Disinstalla**.  
  
3.  Per completare la disinstallazione, riavviare Visual Studio.

