---
title: "Funzionalità di Dotfuscator | Microsoft Docs"
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protezione, community edition, offuscamento, .NET, gratuito, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: "Informazioni sulle funzionalità della versione gratuita di Dotfuscator Community Edition inclusa in Visual Studio 2017."
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
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
ms.sourcegitcommit: 507ff049dae50698d86e1536ed21ab982da1af85
ms.openlocfilehash: fb277e75054f27cbe475acdd21ef4771fbdcde40
ms.lasthandoff: 02/22/2017

---

# <a name="capabilities-of-dotfuscator"></a>Funzionalità di Dotfuscator

Questa pagina illustra le funzionalità di Dotfuscator Community Edition (Dotfuscator CE), con alcuni riferimenti alle opzioni avanzate disponibili tramite gli [aggiornamenti][upgrades].

Dotfuscator è un sistema *post-compilazione* per le applicazioni .NET.
Con Dotfuscator CE, gli utenti di Visual Studio possono [offuscare gli assembly] [ obfuscation] e inserire [difesa attiva] [ checks] e [funzioni di rilevamento per l'analisi] [ analytics] nell'applicazione, senza che Dotfuscator debba accedere al codice sorgente originale.
Dotfuscator protegge l'applicazione in diversi modi, creando una strategia per la protezione a più livelli.

Dotfuscator CE supporta una vasta gamma di tipi assembly e applicazioni .NET, tra cui la [piattaforma UWP (Universal Windows Platform) ] [ uwp] e [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Protezione della proprietà intellettuale

La progettazione, il comportamento e l'implementazione di un'applicazione sono tipi di proprietà intellettuale (IP).
Le applicazioni create per .NET Framework sono però di fatto molto intuitive. È infatti molto facile decompilare gli assembly .NET, [in quanto contengono metadati di alto livello e codice intermedio][assemblies].

Dotfuscator CE include [offuscamento .NET] di base [ obfuscation] sotto forma di [ridenominazione][renaming].
L'offuscamento del codice con Dotfuscator riduce il rischio di accesso non autorizzato al codice sorgente tramite reverse engineering, impedendo che informazioni importanti sulla denominazione rimangano pubbliche.
L'offuscamento contribuisce anche a proteggere il codice dall'esame. Si tratta di un passaggio utile per garantire che l'IP sia legalmente protetto come segreto commerciale.

Molte delle [funzionalità di protezione dell'integrità dell'applicazione](#application-integrity-protection) di Dotfuscator CE possono ostacolare ulteriormente il reverse engineering.
Può succedere ad esempio che un attore non consentito tenti di associare un debugger all'istanza di un'applicazione in esecuzione per comprendere la logica di programma.
Dotfuscator può inserire un [comportamento anti-debug] [ debug] nell'applicazione per bloccare questo tentativo.

## <a name="application-integrity-protection"></a>Protezione dell'integrità dell'applicazione

Oltre a proteggere il codice sorgente, è anche importante assicurare che l'applicazione sia usata come previsto.
Gli utenti malintenzionati possono tentare di assumere il controllo dell'applicazione per aggirare i criteri di licenza (ad esempio, in caso di pirateria), per rubare o manipolare dati sensibili gestiti dall'applicazione o per modificare il comportamento dell'applicazione.

Con Dotfuscator CE è possibile inserire il [codice di convalida dell'applicazione] [ checks] negli assembly, comprese misure [antimanomissione] [ tamper] e [anti-debug] [ debug].
Quando viene rilevato uno stato dell'applicazione non valido, il codice di convalida può [chiamare il codice dell'applicazione per risolvere la situazione nel modo appropriato][check-app].
Oppure, se si preferisce non scrivere codice per gestire gli utilizzi dell'applicazione non validi, è anche possibile inserire con Dotfuscator [report di telemetria] [ check-telemetry] e comportamenti di [risposta] [ check-action] senza che sia necessario modificare il codice sorgente.

Molti di questi stessi metodi possono essere anche usati per applicare le [scadenze finali] [ shelflife] dei software di valutazione.

## <a name="application-monitoring"></a>Monitoraggio delle applicazioni

Quando si sviluppa un'applicazione, è essenziale conoscere i modelli comportamentali degli utenti, inclusi i beta tester e gli utenti di versioni precedenti.
Analizzando l'applicazione è possibile tener traccia della frequenza con cui viene usata e di come viene usata e degli errori riscontrati dagli utenti.

Dotfuscator CE può inserire nell'applicazione codice per il [rilevamento delle eccezioni][exceptions], il [monitoraggio della sessione][sessions] e [il monitoraggio delle funzioni] [ features].
Mentre viene eseguita, l'applicazione elaborata trasmetterà a un [endpoint di PreEmptive Analytics][endpoints] configurato i dati per eseguire l'analisi.

## <a name="see-also"></a>Vedere anche

[Dotfuscator Community Edition User Guide][full] (Guida dell'utente di Dotfuscator CE)

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/articles/standard/assembly-format
[uwp]: https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]: https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]: upgrades.md

[obfuscation]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/obfuscation_overview.html
[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/obfuscation_renaming.html

[analytics]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_overview.html
[endpoints]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_overview.html#endpoints

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_overview.html
[check-app]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_overview.html#app-notification
[check-action]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_overview.html#action

[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/checks_shelflife.html
[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_features.html
[check-telemetry]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/analytics_checks.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/intro_capabilities.html
