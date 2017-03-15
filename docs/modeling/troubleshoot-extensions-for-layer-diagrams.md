---
title: Risoluzione dei problemi di estensioni per diagrammi di dipendenza | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 25
author: alexhomer1
ms.author: ahomer
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 26a1992fb9c49c670740a8d4a9a992df3d0a86db
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Risoluzione dei problemi di estensioni per diagrammi di dipendenza
Questo argomento risolve alcuni problemi che possono verificarsi quando si creano estensioni del modello di livello.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>Quando si preme F5 per eseguire il debug dell'estensione my, my comandi, i gestori movimenti, estensioni di convalida o le proprietà personalizzate non vengono visualizzati nei diagrammi di dipendenza nell'istanza sperimentale di[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  Aprire la soluzione di estensione nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]e il **compilare** menu, fare clic su **Ricompila soluzione**.  
  
2.  Premere **F5** o **CTRL + F5** per avviare l'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aprire un diagramma di dipendenze e testare l'estensione.  
  
 Continuare con la procedura descritta di seguito, se necessario.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Viene seguita una versione precedente dell'estensione.  
  
1.  Assicurarsi che non sia in esecuzione un'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Eliminare la cartella seguente: %LocalAppData%\Microsoft\VisualStudio\\[versione] \ComponentModelCache  
  
    > [!NOTE]
    >  % LocalAppData % corrisponde in genere *DriveName*: \Users\\*nome utente*\AppData\Local..  
  
 Continuare con la procedura descritta di seguito, se necessario.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Viene visualizzata una versione precedente dei risultati di convalida o il metodo di convalida non viene chiamato.  
  
1.  Nell'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]via il **compilare** menu, fare clic su **Pulisci soluzione**. In questo modo vengono cancellati i risultati delle precedenti analisi di convalida memorizzati nella cache.  
  
2.  Assicurarsi che i livelli nel modello siano associati a elementi di codice e che nel modello sia presente almeno un collegamento di dipendenza. La convalida non viene richiamata se non sono presenti elementi da convalidare.  
  
3.  I punti di interruzione normali potrebbero non funzionare in un metodo di convalida, perché è in esecuzione in un processo distinto. È necessario inserire una chiamata a `System.Diagnostics.Debugger.Launch()` se si vuole eseguire il metodo un'istruzione alla volta.  
  
4.  In **source.extension.vsixmanifest** nel progetto di convalida di livello, assicurarsi che sia stato aggiunto un **componente MEF** elemento e un **tipo di estensione personalizzato** elemento sotto **contenuto**.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere i diagrammi di dipendenza](../modeling/extend-layer-diagrams.md)

