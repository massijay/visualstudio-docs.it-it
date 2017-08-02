---
title: Gestione pacchetti in R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93accb9a-1ef8-4806-baa4-02477c2d7ef0
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: a0bc08a5b4e38651e8d62629778e3ab1647e1bcb
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


# <a name="package-manager"></a>Gestione pacchetti

Gestione pacchetti di R Tools per Visual Studio (RTVS) è un'interfaccia utente per la gestione dei pacchetti R. Per aprire questo strumento, selezionare **R Tools > Finestre > Pacchetti** o premere CTRL + 7.

Gestione pacchetti contiene le tre schede descritte di seguito. Tutte le schede visualizzano a sinistra un elenco di pacchetti pertinenti e a destra i dettagli specifici del pacchetto selezionato, ad esempio la versione, la descrizione, la licenza, il percorso di installazione, nonché collegamenti ad altre informazioni pertinenti. La casella di ricerca in alto a destra consente di filtrare l'elenco.

> [!Tip]
> Il termine nella casella di ricerca rimane attivo quando si passa da una scheda all'altra.

- La scheda **Disponibile** consente di sfogliare i pacchetti da installare. Se un pacchetto è già installato, il pulsante **Installa** a destra diventa **Disinstalla**.

    ![Scheda dei pacchetti disponibili in Gestione pacchetti di R Tools per Visual Studio](~/rtvs/media/package-manager-available.png)

- La scheda **Installato** visualizza tutti i pacchetti installati e caricati. Un punto verde accanto a un pacchetto indica che questo è caricato nella sessione di R. Per disinstallare il pacchetto è possibile usare l'icona X di colore rosso nell'elenco a sinistra o il pulsante **Disinstalla** a destra. La freccia di colore blu a destra di un pacchetto installato consente di aggiornare il pacchetto se è disponibile una versione più recente.

    ![Scheda dei pacchetti installati in Gestione pacchetti di R Tools per Visual Studio](~/rtvs/media/package-manager-installed.png)

- La scheda **Caricato** visualizza solo i pacchetti caricati nella sessione di R. Pertanto tutti i pacchetti visualizzati presentano un punto verde. In questa scheda è anche possibile disinstallare e aggiornare i pacchetti.

    ![Scheda dei pacchetti caricati in Gestione pacchetti di R Tools per Visual Studio](~/rtvs/media/package-manager-loaded.png)

## <a name="package-locations"></a>Percorsi dei pacchetti

I pacchetti vengono installati nei percorsi seguenti:

- I pacchetti di base inclusi in RTVS vengono installati in `C:\Program Files\Microsoft\R Client\R_SERVER\library`
- I pacchetti aggiuntivi vengono installati in `%userprofile%\Documents\R\win-library\3.3`

