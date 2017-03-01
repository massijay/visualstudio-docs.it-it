---
title: Estendere i diagrammi di dipendenza | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 39
author: alexhomer1
ms.author: ahomer
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: ad673b1bc7d3089c37717dd7e1f1fce4e86d8100
ms.lasthandoff: 02/22/2017

---
# <a name="extend-dependency-diagrams"></a>Estendere i diagrammi di dipendenza
È possibile scrivere codice per creare e aggiornare i diagrammi di dipendenza e per convalidare la struttura del codice programma in base ai diagrammi di dipendenza in Visual Studio. È possibile aggiungere comandi da visualizzare nel menu di scelta rapida (contestuale) dei diagrammi, personalizzare i movimenti di trascinamento della selezione e accedere al modello di livello dai modelli di testo. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) e distribuirle ad altri utenti di Visual Studio.  
  
 Per ulteriori informazioni sui diagrammi di dipendenza, vedere:  
  
-   [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)  
  
-   [Diagrammi di dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md)  
  
-   [Creare diagrammi di dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="a-nameprereqsa-requirements"></a><a name="prereqs"></a> Requisiti  
 È necessario verificare che nel computer in cui si vogliono sviluppare le estensioni del livello sia installato quanto segue:  
  
-   Visual Studio  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
-   Modeling SDK per Visual Studio  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 È necessario avere installato una versione appropriata di Visual Studio nel computer in cui si vogliono eseguire le estensioni del livello. Per ulteriori informazioni, vedere [distribuire un'estensione di modelli di livello](../modeling/deploy-a-layer-model-extension.md).  
  
 Per informazioni sulle versioni di Visual Studio supportano i diagrammi di dipendenza, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Aggiunta di comandi e movimenti a diagrammi di dipendenza](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [Aggiungere la convalida architettura personalizzati a diagrammi di dipendenza](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [Aggiungere proprietà personalizzate a diagrammi di dipendenza](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [Esplorare e aggiornare i modelli di livello nel codice del programma](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [Distribuire un'estensione del modello di livello](../modeling/deploy-a-layer-model-extension.md)  
  
 [Risoluzione dei problemi di estensioni per diagrammi di dipendenza](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Definire e installare un'estensione di modellazione](../modeling/define-and-install-a-modeling-extension.md)   
 [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)   
 [Diagrammi di dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md)   
 [Creare diagrammi di dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md)   
 [Convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)   

