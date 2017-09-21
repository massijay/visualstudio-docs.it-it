---
title: Personalizzare la compilazione | Microsoft Docs
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 13
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: 86f7fef0365a47e8ea88bc3fc46cb0016efd4628
ms.contentlocale: it-it
ms.lasthandoff: 06/15/2017

---
# <a name="customize-your-build"></a>Personalizzare la compilazione
Nelle versioni di MS Build precedenti alla versione 15, per specificare una nuova proprietà personalizzata per i progetti nella soluzione, è necessario aggiungere manualmente un riferimento a tale proprietà per ogni file di progetto della soluzione. Oppure, è necessario definire la proprietà in un file PROPS e quindi importare in modo esplicito il file PROPS in ogni progetto della soluzione, tra le altre cose.

Tuttavia, ora è possibile aggiungere una nuova proprietà a ogni progetto in un unico passaggio, definendola in un singolo file denominato Directory.Build.props nella radice del repository. Quando si esegue MSBuild, Microsoft.Common.props cerca la struttura di directory per il file Directory.Build.props (e MicrosoftCommon.targets cerca Directory.Build.targets). Se trova la struttura, importa la proprietà. Directory.Build.props è un file definito dall'utente che specifica le personalizzazioni dei progetti in una directory.

## <a name="directorybuildprops-example"></a>Esempio di Directory.Build.props
Ad esempio, per consentire a tutti i progetti di accedere alla nuova funzionalità di Roslyn **/ deterministic** (esposta nella destinazione CoreCompile di Roslyn dalla proprietà `$(Deterministic)`), è possibile eseguire le operazioni indicate di seguito.

1. Creare un nuovo file nella radice del repository denominato Directory.Build.props.
2. Aggiungere al file il seguente codice XML.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Eseguire MSBuild. Le importazioni esistenti del progetto di Microsoft.Common.props e Microsoft.Common.targets trovano il file e lo importano.

## <a name="search-scope"></a>Ambito di ricerca
Quando cerca un file Directory.Build.props, MSBuild scorre la struttura di directory verso l'alto a partire dalla posizione del progetto ($(MSBuildProjectFullPath)), fermandosi quando individua un file Directory.Build.props. Ad esempio, se $(MSBuildProjectFullPath) è c:\users\username\code\test\case1, MSBuild inizia a cercare da quel punto ed esegue la ricerca nella struttura di directory verso l'alto finché non trova un file Directory.Build.props, come nella struttura di directory riportata di seguito.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```
La posizione del file della soluzione è irrilevante per Directory.Build.props.

## <a name="import-order"></a>Ordine di importazione

Directory.Build.props viene importato molto presto in Microsoft.Common.props, quindi le proprietà definite in un secondo tempo non sono disponibili per questo file. Quindi, evitare di fare riferimento a proprietà che non sono ancora state definite (e che verranno restituite come vuote).

Directory.Build.targets viene importato da Microsoft.Common.targets dopo l'importazione dei file TARGET dai pacchetti NuGet. Può quindi essere usato per eseguire l'override di proprietà e destinazioni definite nella maggior parte della logica di compilazione, ma in alcuni casi può essere necessario eseguire personalizzazioni all'interno del file di progetto dopo l'importazione finale.

## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)   

