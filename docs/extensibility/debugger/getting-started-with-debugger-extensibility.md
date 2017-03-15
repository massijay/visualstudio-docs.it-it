---
title: "Introduzione al Debugger estendibilità | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 258fcfcc97d0a6b1455ec60201527cde3e87f9b8
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-debugger-extensibility"></a>Introduzione a estensibilità del Debugger
Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornisce le informazioni necessarie per creare e personalizzare i componenti del debugger per eseguire il debug di programmi dall'interno di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]il debug è aggiunto miglioramenti l'utilizzabilità completa test eseguiti nel precedente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger. È possibile utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug per eseguire un'applicazione in più lingue, oppure è possibile implementare in modo immediato la modifica delle variabili durante il debug di applicazioni e soluzioni in più lingue.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]il debug è eseguita out-of-process con il programma in fase di debug e pertanto è meno intrusivo nello spazio di processo dell'applicazione. Di conseguenza, risulta più semplice scrivere i componenti che interagiscono con il debugger senza modificare il programma di debug.  
  
 Utilizzare al meglio il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], è necessario avere familiarità con il codice seguente:  
  
-   Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE)  
  
-   Il linguaggio di programmazione C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Guida di orientamento per l'estensione del Debugger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Descrive il processo di implementazione del prodotto, a seconda del compilatore e l'output di debug.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componenti, tra cui il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore dei simboli (SH) per il debug.  
  
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il motore di debug (DE) funziona contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressione. Viene descritto, per ognuno dei tre contesti, posizione, posizione o valutazione pertinente a esso.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti alle varie attività di debug, ad esempio un programma di avvio e la valutazione di espressioni.
