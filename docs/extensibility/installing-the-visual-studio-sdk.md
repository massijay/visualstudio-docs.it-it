---
title: L&quot;installazione di Visual Studio SDK | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 722c32c139d2f560fa6d10aba9fd8bac610f9f20
ms.lasthandoff: 03/07/2017

---
# <a name="installing-the-visual-studio-sdk"></a>L'installazione di Visual Studio SDK
Visual Studio SDK è una funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installazione di Visual Studio SDK come parte di un'installazione di Visual Studio  
 Se si desidera includere VSSDK nell'installazione di Visual Studio, è necessario installare il **sviluppo di estensioni di Visual Studio** carico di lavoro in **altri set di strumenti**. Verranno installati Visual Studio SDK, nonché i prerequisiti necessari. È possibile ottimizzare ulteriormente l'installazione, selezionare o visualizzare componenti deselezionando la casella di riepilogo. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>L'installazione di Visual Studio SDK dopo l'installazione di Visual Studio  
 Se si decide di installare Visual Studio SDK dopo aver completato l'installazione di Visual Studio, eseguire nuovamente il programma di installazione di Visual Studio e selezionare il **sviluppo di estensioni di Visual Studio** carico di lavoro.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Installazione da una soluzione di Visual Studio SDK  
 Se si apre una soluzione con un progetto di estensibilità senza prima installare VSSDK, verrà richiesto da una barra informazioni evidenziato sopra Esplora soluzioni. Dovrebbe essere simile al seguente:  
  
 ![SolutionExplorerInstall](~/extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Installazione di Visual Studio SDK dalla riga di comando  
Come per qualsiasi carico di lavoro di Visual Studio o un componente, è possibile installare anche l'elemento dalla riga di comando. Vedere [utilizzare i parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) per informazioni dettagliate su come determinare gli identificatori del carico di lavoro o un componente e le opzioni della riga di comando appropriate.
  
 Si noti che è necessario utilizzare il programma di installazione di Visual Studio che corrisponde alla versione installata di Visual Studio. Ad esempio, se si dispone di Visual Studio Enterprise, installato nel computer, è necessario eseguire il programma di installazione di Visual Studio Enterprise (vs_enterprise.exe).
