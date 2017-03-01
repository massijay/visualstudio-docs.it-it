---
title: Risorse in VS | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 23
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 184642501b9452566a15e1aba30312e17500f7bb
ms.lasthandoff: 02/22/2017

---
# <a name="resources-in-vspackages"></a>Risorse in VS
È possibile incorporare le risorse localizzate in nativa dell'interfaccia utente le DLL satellite, DLL satellite gestite, o in un VSPackage gestito stesso.  
  
 Alcune risorse non possono essere incorporate in VSPackage. I seguenti tipi gestiti possono essere incorporati:  
  
-   Stringhe  
  
-   Chiavi di caricamento del pacchetto (che sono anche stringhe)  
  
-   Icone finestra degli strumenti  
  
-   File di comando tabella Output (CTO) compilati  
  
-   CTO bitmap  
  
-   Guida della riga di comando  
  
-   Sui dati della finestra dialogo  
  
 Selezionare le risorse in un pacchetto gestito l'ID risorsa. Un'eccezione è il file CTO, che deve essere denominato CTMENU. Il file CTO deve essere presente nella tabella delle risorse come un `byte[]`. Tutti gli altri elementi di risorsa sono identificate dal tipo.  
  
 È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>attributo per indicare al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che siano disponibili risorse gestite.</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>  
  
 [!code-cs[N.&1; VSSDKResources](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources n.&1;](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 L'impostazione <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>indica che in questo modo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve ignorare le DLL satellite non gestita durante la ricerca di risorse, ad esempio, utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> </xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rileva due o più risorse aventi lo stesso ID di risorsa, viene utilizzata la prima risorsa viene trovata.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente è una rappresentazione gestita di un'icona di finestra dello strumento.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 Nell'esempio seguente viene illustrato come incorporare la matrice di byte CTO, deve essere denominata CTMENU.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Note di implementazione  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]caricamento di ritardi di VSPackage laddove possibile. È una conseguenza dell'incorporamento di un file CTO in un VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] necessario caricare i package VS tali in memoria durante l'installazione, ovvero quando si compila una tabella unita comando. Le risorse possono essere estratti da un VSPackage esaminando i metadati senza eseguire il codice in VSPackage. VSPackage non viene inizializzato in questa fase, pertanto la riduzione delle prestazioni è minima.  
  
 Quando si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le richieste di una risorsa da un VSPackage dopo l'installazione, tale pacchetto è probabilmente già caricato e inizializzato, pertanto la riduzione delle prestazioni è minimo.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPackages gestito](../../misc/managed-vspackages.md)   
 [La gestione di VSPackage](../../extensibility/managing-vspackages.md)   
 [Risorse localizzate in applicazioni MFC: DLL Satellite](http://msdn.microsoft.com/Library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [VSPackage gestiti](../../misc/managed-vspackages.md)
