---
title: Firma dei pacchetti VSIX | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5a27b4e76e0cd8f986441778ed39c7fbb5a2211
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="signing-vsix-packages"></a>Firma dei pacchetti VSIX
Gli assembly di estensioni non è necessario firmare prima che possano essere eseguite in Visual Studio, ma è consigliabile eseguire questa operazione.  
  
 Se si desidera proteggere l'estensione e assicurarsi che non è stato alterato, è possibile aggiungere una firma digitale a un pacchetto VSIX. Quando un progetto VSIX è firmato, il programma di installazione VSIX verrà visualizzato un messaggio che indica che è firmato, oltre a ulteriori informazioni sulla firma stessa. Se il contenuto del pacchetto VSIX è stato modificato e l'estensione VSIX non è stato nuovamente firmato, il programma di installazione VSIX mostrerà la firma non è valida. L'installazione non è stato arrestato, ma l'utente viene avvisato.  
  
> [!IMPORTANT]
>  A partire da 2015, pacchetti VSIX firmati con un elemento diverso dalla crittografia SHA256 verranno identificati come con una firma non valida. Installazione di VSIX non è bloccata, ma l'utente verrà visualizzato un avviso.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>La firma di un'estensione VSIX con VSIXSignTool  
 È una crittografia SHA256 strumento disponibile dalla firma [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) in nuget.org in [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Utilizzare il VSIXSignTool  
  
1.  Aggiungere l'estensione VSIX a un progetto.  
  
2.  Fare clic con il pulsante destro sul nodo del progetto in Esplora soluzioni selezionare **Aggiungi &#124; Gestisci pacchetti NuGet**.  Per ulteriori informazioni su NuGet e l'aggiunta di vedere pacchetti NuGet, vedere il [documentazione di NuGet](http://docs.microsoft.com/NuGet) e [UI Package Manager](http://docs.microsoft.com/NuGet/Tools/Package-Manager-UI) argomenti.  
  
3.  Cercare VSIXSignTool da VisualStudioExtensibility e installare il pacchetto NuGet.  
  
4.  È ora possibile eseguire il VSIXSignTool dal percorso di pacchetti locali del progetto. Consultare la Guida dello strumento della riga di comando per lo scenario di firma (VSIXSignTool.exe /?).  
  
 Per eseguire l'accesso con una password, ad esempio i file di certificato protetto:  
  
 /F sign VSIXSignTool.exe \<certfile >/p \<password > \<VSIXfile >  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)