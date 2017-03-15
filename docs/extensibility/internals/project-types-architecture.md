---
title: Architettura di tipi di progetto | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: 6
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
ms.openlocfilehash: c9b238f853d7dd3a246f4b3204b15eda34b56885
ms.lasthandoff: 02/22/2017

---
# <a name="project-types-architecture"></a>Architettura di tipi di progetto
In questa sezione contiene informazioni dettagliate sull'architettura dei tipi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)  
 Elenca i servizi che può utilizzare un tipo di progetto e le interfacce che deve implementare.  
  
 [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)  
 Descrive le interfacce di tipi di progetto devono implementare sia possano implementare facoltativamente per fornire funzionalità aggiuntive.  
  
 [Creazione di tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)  
 Consente di decidere quando è necessario creare un progetto di tipo e quando è possibile utilizzare un altro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funzionalità di estendibilità, ad esempio editor e package VS per ottenere lo stesso obiettivo.  
  
 [Selezione e gerarchie](../../extensibility/internals/hierarchies-and-selection.md)  
 Viene descritto come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizza gerarchie e il contesto di selezione per offrire un'esperienza utente coerente e semplificata.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Progetto (sottotipi)](../../extensibility/internals/project-subtypes.md)  
 Viene spiegato come sottotipi di progetto consentono di personalizzare il comportamento dei sistemi di progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Viene fornita una panoramica dei progetti come blocchi predefiniti di base di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come progetti consentono di controllare la creazione e compilazione di codice.
