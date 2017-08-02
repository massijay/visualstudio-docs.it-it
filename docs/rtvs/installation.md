---
title: Installazione di R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ff60292-1b88-4ee9-b2b2-edd957f1a519
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
ms.sourcegitcommit: 90b2481b0ec4f9387fe3a2c0b733a103e8c03845
ms.openlocfilehash: bc0b1112fe6f3acf2605101a863d831f41bb5f6d
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-install-r-tools-for-visual-studio"></a>Come installare R Tools per Visual Studio

Contenuto dell'argomento:

- [Versioni supportate di Visual Studio](#supported-versions-of-visual-studio)
- [Installazione di RTVS in Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Installazione di RTVS in Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Installazione offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Dopo aver installato R Tools, si potrebbe voler configurare Visual Studio per un layout scientifico di dati ottimizzato, come descritto nell'argomento [Options](options.md#data-scientist-layout) (Opzioni).

## <a name="supported-versions-of-visual-studio"></a>Versioni supportate di Visual Studio

R Tools per Visual Studio (RTVS) è supportato nelle edizioni Enterprise, Professional e Community di [Visual Studio 2015 Update 3 (o versioni successive)](http://go.microsoft.com/fwlink/?LinkId=691129) e [Visual Studio 2017](https://www.visualstudio.com/downloads/). 

RTVS non verrà installato se si ha solo Visual Studio Shell incluso in altri prodotti, quali Visual Studio Test Professional e SQL Server Management Studio. Questo avviene perché Visual Studio Shell non ha i componenti necessari per RTVS.


## <a name="installing-rtvs-in-visual-studio-2017"></a>Installazione di RTVS in Visual Studio 2017

> [!Important]
> L'installazione di RTVS in Visual Studio 2017 eseguito in Windows 7 è attualmente bloccata come illustrato in [GitHub issue #3561](https://github.com/Microsoft/RTVS/issues/3561) (Problema n. 3561 in GitHub). Questo problema verrà risolto nell'aggiornamento 15.3 di Visual Studio 2017.

1. Eseguire il programma di installazione di Visual Studio.
2. Selezionare il carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati**:

    ![Carico di lavoro delle applicazioni analitiche e di analisi scientifica dei dati in VS2017](~/docs/rtvs/media/installation-data-science-workload.png)

3. Impostare tutte le opzioni aggiuntive sul lato destro con lo stesso nome del carico di lavoro. Si noti che, per impostazione predefinita, questo carico di lavoro include supporto per F# e Python. Per R, è necessario selezionare minimo **Supporto del linguaggio R**, **Supporto del runtime per lo sviluppo R** e **Microsoft R Client**.

RTVS viene installato in: `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio` in cui `<version>` è generalmente `2017` e `<edition>` è `Community`, `Professional` o `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Installazione di RTVS in Visual Studio 2015

Con Visual Studio 2015, è necessario installare separatamente un interprete di R e R Tools.

### <a name="install-an-r-interpreter"></a>Installare un interprete di R

RTVS richiede un'installazione a 64 bit di R versione 3.2.1 o successiva da una o da più origini seguenti:

* [Microsoft R Open](https://mran.microsoft.com/download/)
* [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
* [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open e CRAN R consentono l'uso di più versioni affiancate. Microsoft R Client supporta solo una versione e userà sempre la versione installata più recentemente.

### <a name="install-the-r-tools"></a>Installare R Tools

Scaricare RTVS corrente da [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current). RTVS verifica la disponibilità di una versione appropriata di Visual Studio e consente anche di installare un interprete di R, se non è già installato.

RTVS viene installato in: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Installazione offline di Visual Studio e RTVS

L'installazione offline è utile per i computer che non sono connessi a Internet:

1. Seguire le istruzioni per creare un programma di installazione offline per la versione di Visual Studio elencata di seguito. 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Installare Visual Studio da un programma di installazione offline.
1. [Scaricare RTVS](https://aka.ms/rtvs-current) e installarlo come di consueto.

## <a name="see-also"></a>Vedere anche

- [Getting started with R](getting-started-with-r.md) (Guida introduttiva a R)
- [R Tools sample projects](getting-started-samples.md) (Progetti di esempio di R Tools)
- [Getting help](getting-started-help.md) (Informazioni di supporto)
- [Option settings](options.md) (Impostazioni delle opzioni)

