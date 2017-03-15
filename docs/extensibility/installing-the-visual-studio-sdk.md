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
ms.sourcegitcommit: 9c25532605613b34ded15a4bd6a533e589b7fce2
ms.openlocfilehash: d039c50cea2ee038baec26fad02a98ae45f0d521
ms.lasthandoff: 02/22/2017

---
# <a name="installing-the-visual-studio-sdk"></a>L'installazione di Visual Studio SDK
A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installazione di Visual Studio SDK come parte di un'installazione di Visual Studio  
 Se si desidera includere VSSDK nell'installazione di Visual Studio, è necessario eseguire un'installazione personalizzata.  
  
> [!NOTE]
>  Nel file eseguibile di installazione, viene chiamato Visual Studio SDK **strumenti di Visual Studio Extensibility**.  
  
1.  Avviare l'installazione di Visual Studio 2015. È possibile installare qualsiasi edizione di Visual Studio, ad eccezione di Express.  
  
2.  Nella prima schermata, selezionare **personalizzato**, non **predefinito**. Scegliere **Avanti**.  
  
3.  Si dovrebbe essere una visualizzazione albero delle caratteristiche personalizzate. Aprire **strumenti comuni**. Dovrebbe essere **strumenti di Visual Studio Extensibility** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Controllare **strumenti di Visual Studio Extensibility** , quindi fare clic su **Avanti** e continuare l'installazione.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>L'installazione di Visual Studio SDK dopo l'installazione di Visual Studio  
 Se si decide di installare Visual Studio SDK dopo aver completato l'installazione di Visual Studio, seguire la procedura seguente:  
  
1.  Passare a **Pannello di controllo / programmi / programmi e funzionalità**e cercare **Visual Studio 2015**. È possibile installare Visual Studio SDK per qualsiasi edizione di Visual Studio 2015, ad eccezione di Express.  
  
2.  Fare doppio clic su **Visual Studio 2015**, quindi fare clic su **modifica**. Verrà visualizzata la pagina di installazione.  
  
3.  Seguire la stessa procedura **l'installazione di Visual Studio SDK come parte di un'installazione di Visual Studio** sopra.  
  
4.  Fare clic su di **strumenti di Visual Studio Extensibility** collegamento per installare Visual Studio SDK.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Installazione da una soluzione di Visual Studio SDK  
 Se si apre una soluzione con un progetto di estensibilità senza prima installare VSSDK, verrà richiesto da una barra informazioni evidenziato sopra Esplora soluzioni. Dovrebbe essere simile al seguente:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Installazione di Visual Studio SDK dalla riga di comando  
 È possibile installare VSSDK dalla riga di comando utilizzando il **/InstallSelectableItems** passare con il programma di installazione di Visual Studio. Per informazioni dettagliate sull'utilizzo dei parametri della riga di comando con il programma di installazione, vedere [utilizzare i parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).  
  
 Di seguito viene illustrato come installare VSSDK automaticamente utilizzando il programma di installazione di Visual Studio 2015 Community:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Si noti che è necessario utilizzare il programma di installazione di Visual Studio che corrisponde alla versione installata di Visual Studio. Ad esempio, se si dispone di Visual Studio Enterprise, installato nel computer, è necessario eseguire il programma di installazione di Visual Studio Enterprise (vs_enterprise.exe).
