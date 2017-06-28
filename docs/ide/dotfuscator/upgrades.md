---
title: Aggiornare Dotfuscator Community Edition (CE) | Microsoft Docs
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protezione, community edition, offuscamento, .NET, gratuito, Visual Studio 2017, aggiornamento, riga di comando
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Informazioni su come eseguire l&quot;aggiornamento di Dotfuscator Community Edition gratuito incluso in Visual Studio 2017.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
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
ms.openlocfilehash: eeabf6db465f57ab373c592b01a682ed6442800f
ms.lasthandoff: 02/22/2017

---

# <a name="upgrade-dotfuscator-community-edition-ce"></a>Aggiornare Dotfuscator Community Edition (CE)

Dotfuscator Community Edition (Dotfuscator CE) mette numerose funzionalità di protezione delle applicazioni e protezione avanzata a disposizione immediata di tutti gli sviluppatori che usano Microsoft Visual Studio.
Gli utenti che eseguono l'aggiornamento della loro versione di Dotfuscator possono tuttavia sfruttare anche altre funzionalità.

## <a name="registering-dotfuscator-ce"></a>Registrazione di Dotfuscator CE

Gli utenti registrati di Dotfuscator CE ottengono l'accesso a funzionalità aggiuntive, ad esempio il [supporto della riga di comando][cli], che rendono più facile l'integrazione di Dotfuscator CE nel processo di compilazione automatico.

La registrazione è veloce, semplice e gratuita.
Per registrare Dotfuscator CE, vedere [la sezione relativa alla registrazione di Dotfuscator CE nella pagina introduttiva del manuale dell'utente completo di Dotfuscator CE][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Mentre Dotfuscator Community Edition offre un livello base di protezione, ***PreEmptive Protection - Dotfuscator* Professional Edition** include trasformazioni di offuscamento e funzionalità di protezione avanzate.
Sono inclusi:

* *Protezione della proprietà intellettuale*
  * Opzioni di ridenominazione aggiuntive, tra cui Enhanced Overload Induction™ e selezione casuale degli identificatori.
  * Strumenti per la decodifica delle analisi dello stack offuscate.
  * Accesso alle trasformazioni di offuscamento a livello aziendale, incluse le [trasformazioni destinate ad annullare la decompilazione automatica del codice][control-flow].
  * La possibilità di [nascondere stringhe sensibili][string-encryption], rendendo impossibile una ricerca semplice del codice decompilato.
  * La possibilità di [incorporare in modo discreto le stringhe di proprietà e distribuzione negli assembly] [ watermarking] (filigrana software), consentendo di determinare l'origine delle perdite di software non autorizzate.
  * La possibilità di [combinare più assembly in uno solo][linking], rendendo ancora più difficile per gli utenti malintenzionati determinare i ruoli degli elementi di codice, poiché è stata eliminata la separazione dei ruoli.
  * La possibilità di [rimuovere automaticamente il codice non usato dall'applicazione][pruning], riducendo la quantità di codice sensibile inviato.
* *Protezione dell'integrità dell'applicazione*
  * [Comportamenti di difesa delle applicazioni][check-actions] aggiuntivi.
  * La possibilità di inserire codice anti-manomissione e anti-debug negli assembly `.dll`.
  * La possibilità di specificare un periodo di avviso prima della scadenza finale di un'applicazione.
  * La possibilità di comunicare il codice dell'applicazione durante un periodo di avviso di scadenza o dopo la scadenza.
  * Crittografia dei dati di telemetria.
* *Monitoraggio delle applicazioni*
  * La possibilità di raccogliere e salvare le informazioni raccolte durante le interruzioni temporanee della rete.
  * La possibilità di raccogliere informazioni personali.
  * Uso illimitato del [rilevamento delle funzioni][features].
  * La possibilità di tenere traccia delle eccezioni rilevate e generate dal codice, oltre alle eccezioni non gestite.
  * La possibilità di tenere traccia delle eccezioni negli assembly `.dll`.
  * Crittografia dei dati di telemetria.

Dotfuscator Professional è l'[obfuscator .NET] [ net-obfuscator] di riferimento del settore ed è adatto per gli sviluppatori aziendali che richiedono supporto, manutenzione e aggiornamenti di prodotto continui.
Dotfuscator Professional offre anche una migliore integrazione con Visual Studio e viene concesso in licenza per uso commerciale.

Per altre informazioni sulle funzionalità di protezione avanzata delle applicazioni di Dotfuscator Professional, visitare la [pagina della panoramica di Dotfuscator] [ product-about] e [il confronto con Community Edition][product-compare].
[Le versioni di valutazione completamente supportate sono disponibili su richiesta sul sito preemptive.com][eval].

## <a name="see-also"></a>Vedere anche

[Questo argomento nel manuale dell'utente completo di Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Check%20Actions.html
[features]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Feature_Usage_Tracking_and_the_Feature_Attribute.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/intro_upgrades.html