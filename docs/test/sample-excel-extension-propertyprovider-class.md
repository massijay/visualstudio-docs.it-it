---
title: 'Estensione Excel di esempio: classe PropertyProvider | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: "9"
ms.author: douge
manager: douge
ms.openlocfilehash: 28cc3774c48eabc240f2f51b9b40f23faba74377
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Estensione Excel di esempio: classe PropertyProvider
Questa classe interna estende la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> e fornisce servizi di proprietà per gli elementi di [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] per la registrazione e la riproduzione dei test dell'interfaccia utente.  
  
## <a name="getcontrolsupportlevel-method"></a>Metodo GetControlSupportLevel  
 Il metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> restituisce un numero che indica il livello di supporto che il provider di proprietà può offrire per il controllo specificato. Più alto è il valore restituito, maggiore è il livello di supporto del controllo offerto dal provider di proprietà. In questo caso, il metodo controlla il valore della proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> del controllo specificato. Se il valore è "Excel" e <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indica che si tratta di un `CellElement`, il metodo restituisce il valore più elevato. In caso contrario, restituisce zero, che indica che non viene fornito alcun supporto.  
  
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
