---
title: Numeri di versione dell&quot;assembly principale e degli assembly satellite localizzati | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 12
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: a41d725b9f58d0f434c3f5169d76988b675aa312
ms.lasthandoff: 02/22/2017

---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Numeri di versione dell'assembly principale e degli assembly satellite localizzati
La classe <xref:System.Resources.SatelliteContractVersionAttribute> offre il supporto al controllo delle versioni per un assembly principale che usa risorse localizzate tramite la gestione risorse. L'applicazione di <xref:System.Resources.SatelliteContractVersionAttribute> all'assembly principale di un'applicazione consente di aggiornare e ridistribuire l'assembly senza aggiornare i relativi assembly satellite. Ad esempio, è possibile usare la classe <xref:System.Resources.SatelliteContractVersionAttribute> con un Service Pack che non introduce nuove risorse senza ricompilare e ridistribuire gli assembly satellite. Affinché le risorse localizzate siano disponibili, la versione del contratto satellite dell'assembly principale deve corrispondere alla classe <xref:System.Reflection.AssemblyVersionAttribute> degli assembly satellite. È necessario specificare un numero di versione esatto in <xref:System.Resources.SatelliteContractVersionAttribute>; non sono consentiti caratteri jolly come "*". Per altre informazioni, vedere [Recupero di risorse](http://msdn.microsoft.com/Library/eca16922-1c46-4f68-aefe-e7a12283641f).  
  
## <a name="updating-assemblies"></a>Aggiornamento degli assembly  
 La classe <xref:System.Resources.SatelliteContractVersionAttribute> consente di aggiornare un assembly principale senza dover aggiornare l'assembly satellite o viceversa. Quando viene aggiornato l'assembly principale, il numero di versione dell'assembly viene modificato. Se si vuole continuare a usare gli assembly satellite esistenti, modificare il numero di versione dell'assembly principale ma lasciare inalterato il numero di versione del contratto satellite. Ad esempio, nel primo rilascio la versione dell'assembly principale potrebbe essere 1.0.0.0. La versione del contratto satellite e la versione dell'assembly per l'assembly satellite saranno ugualmente 1.0.0.0. Se è necessario aggiornare l'assembly principale di un Service Pack, è possibile modificare la versione dell'assembly su 1.0.0.1, mantenendo la versione del contratto satellite e la versione dell'assembly del satellite come 1.0.0.0.  
  
 Se si vuole aggiornare un assembly satellite ma non l'assembly principale, modificare la classe <xref:System.Reflection.AssemblyVersionAttribute> dell'assembly satellite. Insieme all'assembly satellite, sarà necessario inviare un assembly di criteri che informa che il nuovo assembly satellite è compatibile con l'assembly satellite precedente. Per altre informazioni sui criteri, vedere [Come il runtime individua gli assembly](http://msdn.microsoft.com/Library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
 Il codice seguente indica come impostare la versione del contratto satellite. Il codice può essere inserito in uno script di compilazione o nel file AssemblyInfo.vb o AssemblyInfo.cs.  
  
```vb#  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```c#  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Come il runtime individua gli assembly](http://msdn.microsoft.com/Library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)   
 [Impostazione degli attributi dell'assembly](http://msdn.microsoft.com/Library/36a98a81-b5b5-4c19-912a-11f91eff7f4e)   
 [Sicurezza e assembly satellite localizzati](../ide/security-and-localized-satellite-assemblies.md)   
 [Applicazioni localizzate](../ide/localizing-applications.md)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)
