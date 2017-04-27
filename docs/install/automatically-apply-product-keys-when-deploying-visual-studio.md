---
title: Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
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
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: 36a774583f5125ecc09210c9ad5da15ec800f870
ms.lasthandoff: 04/03/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio
È possibile applicare il codice Product Key a livello di programmazione come parte dello script utilizzato per automatizzare la distribuzione di Visual Studio. I codici Product Key possono essere impostati su un dispositivo a livello di programmazione durante l'installazione di Visual Studio o al termine dell'installazione.  

## <a name="apply-the-license-during-installation"></a>Applicare la licenza durante l'installazione  
 Usare il parametro `--productKey` per applicare un codice Product Key durante il processo di installazione di Visual Studio. Questo parametro di installazione può essere usato con il parametro `--quiet parameter` per installare Visual Studio in uno stato già concesso in licenza per un utente finale. Per usare il parametro `--productKey`, aprire un prompt dei comandi. Eseguire il programma di installazione (ad esempio, vs_enterprise.exe o vs_professional.exe) e impostare il parametro `--productKey` con un codice Product Key (25 caratteri) con o senza trattini:  

 Questo è un comando di esempio per l'installazione di Visual Studio 2015 Enterprise con il codice Product Key AAAAABBBBBCCCCCDDDDDEEEEEEE:  

 `vs_enterprise.exe [any other setup parameters] --productKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  

## <a name="apply-the-license-after-installation"></a>Applicare la licenza dopo l'installazione  
 È possibile attivare una versione installata di Visual Studio con un codice Product Key tramite l'utilità storePID.exe nei computer di destinazione in modalità invisibile all'utente. StorePID.exe è un programma di utilità che viene installato con Visual Studio in **\<unità>:\\\Programmi (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe**.  

 Eseguire storePID.exe con privilegi elevati, usando un agente System Center o un prompt dei comandi con privilegi elevati, seguito dal codice Product Key (con i trattini) e il codice Microsoft Product Code (MPC). Assicurarsi di includere i trattini nel codice Product Key.  

 `StorePID.exe [product key including the dashes] [MPC]`  

 Questa è una riga di comando di esempio per l'installazione di Visual Studio 2017 Enterprise, con MPC uguale a 08860 e un codice Product Key "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE":  

 `C:\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860`  

 La tabella seguente riporta i codici MPC per ogni edizione di Visual Studio:  

|Edizione di Visual Studio | MPC |  
|---------------------------|---------|
|Visual Studio Enterprise 2017|08860|  
|Visual Studio Professional 2017|08862|  
|Visual Studio Test Professional 2017|08866|
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  

Se StorePID.exe ha applicato correttamente il codice Product Key, verrà restituito 0. Se si verificano errori, verrà restituito un numero compreso tra 1 e 6.  

## <a name="see-also"></a>Vedere anche  
 * [Installare Visual Studio](../install/install-visual-studio.md)
 * [Creare un'installazione offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)

