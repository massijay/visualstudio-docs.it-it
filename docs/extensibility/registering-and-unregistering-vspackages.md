---
title: Registrazione e annullamento della registrazione di package VS | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
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
ms.openlocfilehash: 73039d6e9bf0db6b3deee00745e21660173f21c0
ms.lasthandoff: 02/22/2017

---
# <a name="registering-and-unregistering-vspackages"></a>Package VS della registrazione e annullamento della registrazione
Utilizzare gli attributi per registrare un VSPackage, ma  
  
## <a name="registering-a-vspackage"></a>Registrazione di un VSPackage  
 È possibile utilizzare gli attributi per controllare la registrazione di VSPackages gestito. Tutte le informazioni di registrazione sono contenute in un file. pkgdef. Per ulteriori informazioni sulla registrazione basata su file, vedere [CreatePkgDef utilità](../extensibility/internals/createpkgdef-utility.md).  
  
 Il codice seguente viene illustrato come utilizzare gli attributi di registrazione standard per registrare il pacchetto Visual Studio.  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Annullamento della registrazione di un'estensione  
 Se si desidera rimuoverli dall'istanza sperimentale provato con molta VSPackage diversi, è possibile eseguire semplicemente il **reimpostare** comando. Cercare **Reimposta l'istanza sperimentale di Visual Studio** nella pagina di avvio del computer, o eseguire questo comando dalla riga di comando:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Se si desidera disinstallare un'estensione che è stato installato l'istanza di sviluppo di Visual Studio, passare alla **strumenti / estensioni e aggiornamenti**, trovare l'estensione e fare clic su **Disinstalla**.  
  
 Se per qualche motivo nessuno di questi metodi ha esito positivo alla disinstallazione dell'estensione, è possibile annullare la registrazione di assembly VSPackage dalla riga di comando come indicato di seguito:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Package VS](../extensibility/internals/vspackages.md)
