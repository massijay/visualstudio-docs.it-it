---
title: 'Estensione Excel di esempio: classe PropertyProvider | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
ms.author: douge
manager: douge
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
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 99397f8f0c6e0e261451cae642cf6e48fe5bba56
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-propertyprovider-class"></a>Estensione Excel di esempio: classe PropertyProvider
Questa classe interna estende la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> e fornisce servizi di proprietà per gli elementi di [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] per la registrazione e la riproduzione dei test dell'interfaccia utente.  
  
## <a name="getcontrolsupportlevel-method"></a>Metodo GetControlSupportLevel  
 Il metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> restituisce un numero che indica il livello di supporto che il provider di proprietà può offrire per il controllo specificato. Più alto è il valore restituito, maggiore è il livello di supporto del controllo offerto dal provider di proprietà. In questo caso, il metodo controlla il valore della proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> del controllo specificato. Se il valore è "Excel" e <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indica che è un `CellElement`, il metodo restituisce il valore più elevato. In caso contrario, restituisce zero, che indica che non viene fornito alcun supporto.  
  
## <a name="getpropertynames-method"></a>Metodo GetPropertyNames  
 Restituisce un dizionario di nomi di proprietà e descrittori di proprietà per le proprietà supportate di un controllo di cella di Excel.  
  
## <a name="getpropertydescriptor-method"></a>Metodo GetPropertyDescriptor  
 Questo metodo viene chiamato dal framework di test per ottenere il descrittore di proprietà predefinito per il nome di proprietà specificato.  
  
## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Metodi GetPropertyValue e SetPropertyValue  
 Il metodo `GetPropertyValue` usa la classe `Communicator` dell'estensione per restituire il valore della proprietà da Excel. Il metodo `SetPropertyValue` usa la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> e il componente `Communicator` per impostare il valore della proprietà. Questi metodi vengono chiamati dal framework di test.  
  
## <a name="code-generation-customization-methods"></a>Metodi di personalizzazione della generazione di codice  
 Questi metodi non sono implementati per questa estensione. Di conseguenza, restituiscono `null` o generano l'eccezione <xref:System.NotImplementedException>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

