---
title: Personalizzazione della pagina iniziale per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 45
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
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 102091f8214b822a5b6be1c93f913d6ddbcd8d9b
ms.contentlocale: it-it
ms.lasthandoff: 05/24/2017

---
# <a name="customize-the-start-page-for-visual-studio"></a>Personalizzazione della pagina iniziale per Visual Studio
È possibile personalizzare la pagina iniziale di Visual Studio con diverse modalità predefinite, ad esempio facendo in modo che visualizzi la finestra di dialogo **Apri progetto** o che apra la soluzione caricata più di recente. È inoltre possibile visualizzare una pagina iniziale personalizzata, ovvero una pagina XAML Windows Presentation Foundation (WPF) che viene eseguita in una finestra dello strumento e che può eseguire comandi interni a Visual Studio.  

## <a name="customize-the-default-start-page"></a>Personalizzare la pagina iniziale predefinita  

1.  Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  

2.  Espandere **Ambiente**, quindi scegliere **Avvio**.  

3.  Nell'elenco **At startup** (All'avvio), scegliere l'elemento corrispondente alla personalizzazione desiderata.  

## <a name="show-a-custom-start-page"></a>Visualizzare una pagina iniziale personalizzata  

1.  Installare una pagina iniziale personalizzata in uno dei modi seguenti:  

    -   Installarla da [Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), da un altro sito Web o da una pagina nell'Intranet locale.  

        Aprire un file .vsix contenente una pagina iniziale personalizzata oppure copiare e incollare i file della pagina iniziale nella cartella **%USERPROFILE% \Documenti\Visual Studio 2017\StartPages** nel computer.  

    -   Creare una pagina iniziale personalizzata se è stato installato Visual Studio SDK.  

         Vedere [Creazione di una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).  

2.  Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  

3.  Espandere **Ambiente**, quindi scegliere **Avvio**.  

4.  Nell'elenco **Personalizza pagina iniziale** scegliere la pagina desiderata.  

> [!NOTE]
>  Se un errore in una pagina iniziale personalizzata determina un arresto anomalo di Visual Studio, è possibile avviare Visual Studio in modalità sicura e quindi impostarne l'utilizzo della pagina iniziale predefinita. Vedere [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  

## <a name="see-also"></a>Vedere anche  
 [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md)   

