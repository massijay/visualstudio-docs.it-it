---
title: Firma dei pacchetti VSIX | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 12
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: da489f0fd0483cddbefb2899eb91bd1d56735d62
ms.lasthandoff: 02/22/2017

---
# <a name="signing-vsix-packages"></a>Firma dei pacchetti VSIX
Gli assembly di estensioni non è necessario firmare prima che vengano eseguiti in Visual Studio, ma è consigliabile farlo.  
  
 Se si desidera proteggere l'estensione e assicurarsi che non è stato alterato, è possibile aggiungere una firma digitale a un pacchetto VSIX. Quando un progetto VSIX è firmato, il programma di installazione VSIX verrà visualizzato un messaggio per indicare che viene eseguito, con ulteriori informazioni sulla firma stessa. Se il contenuto del pacchetto VSIX è stato modificato e non è stato firmato nuovamente il progetto VSIX, il programma di installazione VSIX mostrerà che la firma non è valida. L'installazione non è stato arrestato, ma l'utente viene avvisato.  
  
> [!IMPORTANT]
>  A partire da 2015, i pacchetti VSIX firmati utilizzando un valore diverso da crittografia SHA256 verranno identificati come avente una firma non valida. Installazione di VSIX non è bloccata, ma l'utente verrà visualizzato l'avviso.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>La firma di un progetto VSIX con VSIXSignTool  
 Esiste una crittografia SHA256 firma strumento disponibile da [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) su nuget.org in [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Utilizzare il VSIXSignTool  
  
1.  Aggiungere il progetto VSIX per un progetto.  
  
2.  Fare clic con il pulsante destro sul nodo del progetto in Esplora soluzioni, selezionare **Aggiungi | Gestisci pacchetti NuGet**.  Per ulteriori informazioni su NuGet e aggiungere NuGet pacchetti vedere [NuGet Panoramica](http://docs.nuget.org/) e [la gestione di pacchetti NuGet mediante la finestra di dialogo](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3.  Cercare VSIXSignTool da VisualStudioExtensibility e installare il pacchetto NuGet.  
  
4.  È ora possibile eseguire il VSIXSignTool dal percorso locale di pacchetti del progetto. Consultare la Guida dello strumento della riga di comando per lo scenario di firma (VSIXSignTool.exe /?).  
  
 Ad esempio per accedere con un file di certificato protetto password:  
  
 /F sign VSIXSignTool.exe \<certfile > / p \<password > \<VSIXfile >  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
