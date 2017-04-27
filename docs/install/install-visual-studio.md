---
title: Installare Visual Studio 2017 | Microsoft Docs
description: Informazioni dettagliate sull&quot;installazione di Visual Studio.
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
ms.assetid: 8d4297e4-9f43-4f12-95ec-22e61154480e
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: 47688935cec36db174c3a0c424b1705ae47c6118
ms.lasthandoff: 04/03/2017

---
# <a name="install-visual-studio-2017"></a>Installare Visual Studio 2017
In questo articolo viene presentato un nuovo modo per installare Visual Studio! Nella versione più recente è stata semplificata la procedura che consente di selezionare e installare solo le funzionalità necessarie. È anche stato ridotto il footprint minimo di Visual Studio in modo che possa essere installato più rapidamente, limitando l'impatto sul sistema.  

 Per altre informazioni sulle novità, vedere le [note sulla versione](https://www.visualstudio.com/news/releasenotes/vs15-relnotes) Microsoft. Per informazioni più dettagliate sulla riprogettazione dell'esperienza di installazione, vedere i post di blog Microsoft "[Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)" (Programma di installazione di Visual Studio più rapido e più semplice) e "[Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)" (Anatomia di un'istallazione di Visual Studio a basso impatto).  

 Tutto pronto? Sarà illustrata una procedura dettagliata. Ma veniamo al dunque.  

## <a name="install-the-installer"></a>Installare il programma di installazione  
 Con il download di Visual Studio 2017 viene scaricato un programma di bootstrap che installa a sua volta il nuovo programma di installazione semplificato. Questo nuovo programma di installazione include tutto il necessario per personalizzare l'installazione.  

> [!IMPORTANT]
> Se nel computer è installata una versione di anteprima di Visual Studio 2017, verrà chiesto di rimuoverla prima di installare Visual Studio 2017.

1.  **[Scaricare Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)** e fare clic su **Salva**. Dalla cartella **Download** eseguire quindi il file del programma di bootstrap corrispondente all'edizione scelta.

  * **vs_enterprise.exe** per Visual Studio Enterprise
  * **vs_professional.exe** per Visual Studio Professional
  * **vs_community.exe** per Visual Studio Community  <br><br>

  Se si riceve una comunicazione di Controllo dell'account utente, fare clic su **Sì**.  

2.  Verrà richiesto di confermare le [Condizioni di licenza](https://www.visualstudio.com/license-terms/) e l'[Informativa sulla privacy](https://go.microsoft.com/fwlink/?LinkID=824704) di Microsoft. Fare clic su **Installa** per continuare.  

   ![Condizioni di licenza e informativa sulla privacy](media/vs2017-privacy-and-license-terms.PNG "Condizioni di licenza e informativa sulla privacy")  

3.  Nelle diverse schermate di stato viene visualizzato l'avanzamento dell'installazione. Al termine dell'installazione, è possibile selezionare i set di funzionalità, o i carichi di lavoro, che si vuole installare.

## <a name="install-workloads"></a>Installare i carichi di lavoro  
 A questo punto, è possibile personalizzare l'installazione usando i carichi di lavoro. Selezionare uno o più carichi di lavoro. Ogni carico di lavoro contiene le funzionalità necessarie per il linguaggio di programmazione o la piattaforma che si preferisce.  

 Di seguito viene illustrato come ottenerli.  

1.  Individuare il carico di lavoro che si vuole installare nella schermata d'**installazione di Visual Studio**.  

  ![Finestra di dialogo di installazione di Visual Studio 2017](media/vs2017-workloads.PNG "Installazione di Visual Studio 2017")

     Scegliere ad esempio il carico di lavoro Sviluppo per desktop .NET. Include l'editor principale predefinito che offre supporto di base per la modifica del codice per oltre 20 linguaggi, la possibilità di aprire e modificare il codice da qualsiasi cartella senza che sia necessario un progetto e il controllo del codice sorgente integrato.  

2.  Dopo aver selezionato il carico di lavoro, fare clic su **Installa**.  

    A questo punto si apriranno diverse schermate di stato in cui sarà visualizzato l'avanzamento dell'installazione di Visual Studio.

3.  Dopo aver installato i carichi di lavoro e i componenti nuovi, fare clic su **Avvia**.

## <a name="install-individual-components"></a>Installare i singoli componenti

Se non si vuole usare la comoda funzionalità Carichi di lavoro per personalizzare l'installazione di Visual Studio, scegliere l'opzione **Singoli componenti** dal programma di installazione di Visual Studio, selezionare i componenti desiderati e seguire le istruzioni visualizzate.

  ![Visual Studio 2017 - Installare singoli componenti](media/vs2017-workloads.PNG "Installare singoli componenti di Visual Studio")

## <a name="install-language-packs"></a>Installare i Language Pack

Per installare Visual Studio 2017 nella lingua prescelta, fare clic sull'opzione **Language Pack** dal programma di installazione di Visual Studio e seguire le istruzioni visualizzate.

  ![Visual Studio 2017 - Installare Language Pack](media/vs2017-languages.PNG "Installare Language Pack di Visual Studio")

### <a name="change-the-installer-language"></a>Modificare la lingua del programma di installazione

Per impostazione predefinita, alla prima esecuzione il programma di installazione tenta di trovare una corrispondenza con la lingua del sistema operativo. Il programma di installazione memorizza questa impostazione che è tuttavia possibile modificare eseguendo il programma di installazione dalla riga di comando. Ad esempio, usare il comando seguente per forzare l'esecuzione in inglese del programma di installazione: `vs_installer.exe --locale en-US`. Il programma di installazione memorizza questa impostazione per l'esecuzione successiva. Il programma di installazione supporta i token delle lingue seguenti: zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES e tr-TR.

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere l'articolo [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](https://support.microsoft.com/help/4015967/troubleshooting-visual-studio-2017-installation-and-upgrade-failures) della Knowledge Base che include suggerimenti utili per la risoluzione dei problemi.

## <a name="see-also"></a>Vedere anche  
* [Modificare Visual Studio 2017](modify-visual-studio.md)
* [Disinstallare Visual Studio 2017](uninstall-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Come segnalare un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

