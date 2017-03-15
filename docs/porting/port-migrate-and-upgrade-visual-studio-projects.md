---
title: Conversione, migrazione e aggiornamento dei progetti di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: ae6564f10ca561853444698665779bd1014d4afd
ms.openlocfilehash: 2915a9ceec638471ac29599992a7ccdff17cefb4
ms.lasthandoff: 02/22/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Conversione, migrazione e aggiornamento dei progetti di Visual Studio
Quando si passa a una versione più recente di Visual Studio, è importante sapere se è necessario modificare soluzioni, progetti, file e altre risorse create in versioni precedenti *prima* di eseguirle nelle versioni più recenti.

 Molte delle risorse usate più di frequente si comportano in Visual Studio 2017 RC (la versione più recente) come si comportavano nella versione precedente, Visual Studio 2015, e nelle due versioni ancora precedenti, Visual Studio 2013 e Visual Studio 2012.

 In Visual Studio 2017 RC, ad esempio, è possibile aprire un progetto creato in Visual Studio 2015 o Visual Studio 2013, modificarlo e quindi riaprirlo in Visual Studio 2017 RC; le modifiche persistono e il comportamento del progetto è analogo a quello della versione precedente. Lo stesso vale per molte risorse create in Visual Studio 2012.  

 Se si usa Visual Studio 2015 con Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1, è possibile creare e modificare i progetti e i file in una qualsiasi di queste versioni. È possibile trasferire i progetti e i file tra le versioni purché non si aggiungono funzionalità che non sono supportate da una delle versioni. (Per altre informazioni sulle funzionalità specifiche di ogni versione, vedere le [Note sulla versione](https://www.visualstudio.com/vs/release-notes/).)

