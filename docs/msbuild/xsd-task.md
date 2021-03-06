---
title: "Attività XSD | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: df309f6b4d28da051dca9b824d06dcae221b2a9e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="xsd-task"></a>Attività XSD
Esegue il wrapping dello strumento XML Schema Definition (xsd.exe), che genera file di schema o di classe da un'origine.  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente descrive i parametri dell'attività **XSD**.  
  
-   **AdditionalOptions**  
  
     Parametro **String** facoltativo.  
  
     Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, "*/opzione1 /opzione2 /opzione#*". Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **XSD**.  
  
-   **GenerateFromSchema**  
  
     Parametro **String** facoltativo.  
  
     Specifica i tipi generati dallo schema specificato.  
  
     Specificare uno dei valori seguenti, ognuno dei quali corrisponde a un'opzione XSD.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Lingua**  
  
     Parametro **String** facoltativo.  
  
     Specifica il linguaggio di programmazione da usare per il codice generato.  
  
     È possibile scegliere tra **CS** (C#, il linguaggio predefinito), **VB** (Visual Basic) o **JS** (JScript). È anche possibile specificare un nome completo per una classe che implementa `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
-   **Namespace**  
  
     Parametro **String** facoltativo.  
  
     Specifica lo spazio dei nomi del runtime per i tipi generati.  
  
-   **Sources**  
  
     Parametro `ITaskItem[]` obbligatorio.  
  
     Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.  
  
-   **SuppressStartupBanner**  
  
     Parametro **Boolean** facoltativo.  
  
     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.  
  
-   **TrackerLogDirectory**  
  
     Parametro **String** facoltativo.  
  
     Specifica la directory per il log di Tracker.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)