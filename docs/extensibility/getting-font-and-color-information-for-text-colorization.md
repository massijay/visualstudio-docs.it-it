---
title: Recupero di tipo di carattere e colore per testo colorazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 22
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 57b3d53f86d132779fb00608886fa7c479b71551
ms.lasthandoff: 04/05/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Recupero di tipo di carattere e colore per testo colorazione
Il processo che esegue il rendering o Visualizza colorato testo negli elementi dell'interfaccia utente dipende dal tipo di progetto, la tecnologia e developer di preferenze. Il **tipi di carattere e colori** pagina delle proprietà vengono archiviate le impostazioni.  
  
 La maggior parte delle implementazioni che visualizzano testo colorato necessario il `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` e associate le interfacce per le impostazioni di visualizzazione di presentazione, il recupero e l'archiviazione di testo.  
  
> [!NOTE]
>  Quando si personalizza l'editor di componenti di base (che supporta il **EditorCategory testo**), è consigliabile utilizzare la tecnologia di colorazione nel servizio di linguaggio. Per ulteriori informazioni, vedere [tipo di carattere e colore Panoramica](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Recupero di informazioni di colore e tipo di carattere predefinito  
 Tutti i **tipi di carattere e colori** le impostazioni di qualsiasi finestra di visualizzazione di testo devono essere specificate nel **elementi visualizzati** di uno **categoria**. Per ulteriori informazioni, vedere [tipi di carattere e colori, ambiente, finestra di dialogo Opzioni](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Per colorare, un pacchetto VSPackage deve ottenere corrente **tipi di carattere e colori** impostazioni. Un pacchetto VSPackage può scopo nei modi seguenti, a seconda delle esigenze:  
  
-   Utilizzare il meccanismo di persistenza di carattere e colori per recuperare lo stato corrente o archiviato. Per ulteriori informazioni, vedere [accesso archiviati tipo di carattere e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>interfaccia di un servizio che fornisce i dati di carattere e colori per ottenere un'istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, se il pacchetto VSPackage non sia anche il provider di carattere e colori.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
-   Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
 Per garantire che i risultati ottenuti tramite polling sono aggiornate, potrebbe essere utile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>interfaccia per determinare se è necessario eseguire un aggiornamento prima di chiamare i metodi di recupero del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
 Dopo l'acquisizione di informazioni di carattere e colori, analizzare il testo da visualizzare per identificare quelli che richiedono la colorazione e quindi visualizzare il testo della finestra utilizzando i tipi di carattere appropriati e i colori.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Utilizzo di tipi di carattere e testo](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Utilizzo dei colori](/cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (interfaccia graphics device)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
