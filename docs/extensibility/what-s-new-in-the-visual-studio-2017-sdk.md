---
title: "Novità di Visual Studio 2017 SDK | Documenti di Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: 1
author: gregvanl
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 3da360fc4df5516f5d976f807319c07b49d8c4e8
ms.contentlocale: it-it
ms.lasthandoff: 03/07/2017

---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Novità di Visual Studio 2017 SDK

Visual Studio SDK include le seguenti funzionalità nuove e aggiornate per Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato v3 VSIX

Per supportare la nuova installazione leggera di Visual Studio 2017, il formato di manifesto dell'estensione VSIX è stato aggiornato alla versione 3 (v3 VSIX).

Il nuovo formato include il supporto per:

* Dichiarare in modo esplicito i prerequisiti per essere rilevati e installati per il VSIXInstaller.
* Assembly Ngen sull'installazione dell'estensione.
* L'installazione di risorse all'esterno di radice dell'estensione consueto.

Per ulteriori informazioni su queste modifiche, vedere gli argomenti seguenti:

* [Modifiche all'estendibilità per 2017](breaking-changes-2017.md)
* [Supporto di Ngen in VSIX v3](ngen-support.md)
* [Installazione all'esterno della cartella delle estensioni](set-install-root.md)
* [Domande frequenti relative all'estensibilità di Visual Studio 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Migrazione progetto extensibility di Visual Studio 2017

Per informazioni su come aggiornare i progetti di estendibilità e i relativi manifesti VSIX a Visual Studio 2017, vedere [procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="lightweight-solution-load-lsl"></a>Carico soluzione semplificata (LSL)

Carico soluzione semplice è una nuova funzionalità di Visual Studio 2017 che riduce significativamente il tempo di caricamento di soluzione, che consente di essere più produttivi più rapidamente. Quando è necessario LSL è abilitato, Visual Studio non verrà completamente caricato progetti fino a quando non si inizia a utilizzarli.

LSL può influire estensioni di Visual Studio. Estensioni le cui funzionalità dipendono da un progetto completamente caricato potrebbero non funzionare o funzionare nel modo corretto. Vedere [carico soluzione Lightweight](lightweight-solution-load-extension-impact.md) sapere se l'estensione potrebbe avere effetti e ottenere istruzioni sull'aggiornamento dell'estensione.

## <a name="custom-project-and-item-templates"></a>Modelli di progetto e di elemento personalizzati

A partire da Visual Studio 2017, la ricerca di progetto personalizzati e modelli di elemento sarà non verrà eseguita. Al contrario, l'estensione deve fornire i file di manifesto modello che descrivono il percorso di installazione di questi modelli. È possibile utilizzare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione usando un file MSI, è necessario generare manualmente i file manifesto del modello. Per ulteriori informazioni, vedere [aggiornamento progetto personalizzato e i modelli di Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Lo schema del manifesto del modello è documentato in [Visual Studio modello Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Linee guida estensione aggiornata

C'è una nuova [procedura: diagnosticare le prestazioni di estensione](how-to-diagnose-extension-performance.md) argomento nella sezione [gestione package VS](managing-vspackages.md) per mostrare come rilevare e analizzare l'impatto di estensione in Visual Studio avvio e soluzione tempi di caricamento.

