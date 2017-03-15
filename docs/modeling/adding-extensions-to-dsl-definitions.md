---
title: Aggiunta di estensioni alle definizioni DSL | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: f335db9f22392c4d0293a51111efff88c25c3145
ms.lasthandoff: 02/22/2017

---
# <a name="adding-extensions-to-dsl-definitions"></a>Aggiunta di estensioni alle definizioni DSL
Estensione di definizione DSL consente di creare un pacchetto di estensioni per un linguaggio specifico di dominio (DSL). Può installare l'estensione di DSL, incluso in Visual Studio Integration Extension (VSIX), nel computer dell'utente nello stesso modo come un linguaggio DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate in fase di esecuzione in modo dinamico. Linguaggi specifici di dominio non deve essere progettato in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terze parti senza alterare il DSL esteso.  
  
 Le funzionalità aggiuntive possono includere quanto segue:  
  
-   Proprietà degli elementi di modello e la presentazione  
  
-   Elementi Decorator per forme e connettori  
  
-   Classi, le relazioni, forme e connettori  
  
-   Vincoli di convalida  
  
-   Schede ed elementi della casella degli strumenti  
  
 Un utente di un DSL estesa può creare e salvare un modello che contiene le istanze di funzionalità aggiuntive e questi possono essere letti da altri utenti che hanno installato l'estensione appropriata. Gli utenti che non hanno installato l'estensione non possono utilizzare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche  
 [Post di blog correlati](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

