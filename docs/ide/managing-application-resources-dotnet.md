---
title: Gestione delle risorse delle applicazioni (.NET) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 5cb2e044f5c55881adade6d3022fc453360a2e9c
ms.contentlocale: it-it
ms.lasthandoff: 05/30/2017

---
# <a name="managing-application-resources-net"></a>Gestione delle risorse delle applicazioni (.NET)
I file di risorse sono file che fanno parte di un'applicazione ma non vengono compilati, ad esempio file di icone o file audio. Poiché questi file non fanno parte del processo di compilazione, è possibile modificarli senza dover ricompilare i file binari. Se si prevede di localizzare l'applicazione, è consigliabile usare file di risorse per tutte le stringhe e le altre risorse che devono essere modificate quando si localizza l'applicazione.  
  
 Per altre informazioni sulle risorse nelle app desktop .NET, vedere [Risorse nelle applicazioni desktop](/dotnet/framework/resources/index). Per altre informazioni sulle risorse nelle app desktop C++, vedere [Working with Resource Files](/cpp/windows/working-with-resource-files).  
  
 Le app di Windows Store usano un modello di risorse diverso rispetto alle app desktop. Per informazioni sulle risorse nelle app di Windows Store, vedere [Definizione delle risorse delle applicazioni](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx) sul sito Web Windows Dev Center.  
  
## <a name="working-with-resources"></a>Uso delle risorse  
 Aprire la finestra delle proprietà del progetto in un progetto di codice gestito. A questo scopo, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà**oppure digitare **proprietà del progetto** nella finestra **Avvio veloce** o premere ALT+INVIO nella finestra **Esplora soluzioni** . Selezionare la scheda **Risorse** . È possibile aggiungere un file RESX, se non è ancora presente nel progetto, aggiungere ed eliminare diversi tipi di risorse e modificare le risorse esistenti.  
  
 Per informazioni su come usare le risorse nei progetti C++, vedere [How to: Create a Resource](/cpp/windows/how-to-create-a-resource) (Procedura: Creare una risorsa).
