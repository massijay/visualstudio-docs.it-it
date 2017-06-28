---
title: 'Estensione Excel di esempio: classe TechnologyManager | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
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
ms.openlocfilehash: 07e37b1a1d7b02992bb4da69bd158878095dd789
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-technologymanager-class"></a>Estensione Excel di esempio: classe TechnologyManager
Questa classe estende la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> ed è responsabile di fornire i servizi di base per l'estensione [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]. Benché la classe di base disponga di numerosi metodi, in questo esempio ne viene usato solo un sottoinsieme.  
  
 Alcuni metodi restituiscono solo un valore di proprietà. Molti metodi sono progettati per consentire allo sviluppatore di eseguire l'override degli algoritmi predefiniti incorporati nel modulo dei test codificati dell'interfaccia utente. Questi metodi generano un'eccezione <xref:System.NotSupportedException> o restituiscono `null`, che indica al framework di usare l'algoritmo predefinito.  
  
 A seconda della complessità della tecnologia sottostante, lo sviluppo del codice del gestore della tecnologia potrebbe richiedere da alcune settimane a qualche mese. Excel offre l'opportunità di creare un gestore della tecnologia potenzialmente molto esteso. Questo esempio è intenzionalmente limitato alle celle e ai fogli di lavoro di Excel e usa una formattazione limitata.  
  
 Quando possibile, il codice del gestore della tecnologia usa il canale di Servizi remoti .NET aperto tramite la classe `Communicator` per estrarre informazioni dal componente aggiuntivo in esecuzione nel processo di Excel.  
  
## <a name="com-visibility"></a>Visibilità COM  
 Si noti che questa classe e tutte le classi dell'elemento che estendono la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> dispongono di <xref:System.Runtime.InteropServices.ComVisibleAttribute> con un valore di `true` per garantire che le classi siano visibili a COM.  
  
## <a name="technologyname-property"></a>Proprietà TechnologyName  
 L'override della proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> deve fornire un nome univoco e significativo che identifichi la tecnologia sottostante per tutti gli altri componenti dell'estensione. Per questa estensione, il valore è "Excel".  
  
## <a name="getcontrolsupportlevel-method"></a>Metodo GetControlSupportLevel  
 L'override del metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> restituisce un numero che indica il livello di supporto che il gestore della tecnologia può offrire per il controllo rappresentato dall'handle specificato. Più alto è il valore restituito, maggiore è il livello di supporto del controllo offerto dal gestore della tecnologia. In questo caso, il metodo controlla la finestra che contiene il controllo. Se si tratta di un foglio di lavoro di Excel, il metodo restituisce il valore massimo. In caso contrario, restituisce zero, che indica che non viene fornito alcun supporto.  
  
## <a name="methods-to-get-an-element"></a>Metodi per ottenere un elemento  
 Esistono diversi metodi importanti usati dal framework dei test codificati dell'interfaccia utente per ottenere un elemento specifico della tecnologia, fornendo un handle, un punto sullo schermo o un elemento da una tecnologia diversa. Il codice per questi metodi è di facile comprensione. I metodi di base sono i seguenti:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>Metodo ParseQueryId  
 Quando viene creato un test codificato dell'interfaccia utente, l'utente può specificare i valori delle proprietà per alcuni o tutti i controlli nel test. Questi valori di proprietà vengono usati dal framework di test per creare coppie nome-valore, definite proprietà di ricerca, usate per trovare gli specifici controlli dell'interfaccia utente durante il test. L'insieme di tutte le proprietà di ricerca rappresenta il valore della proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> di ogni elemento della tecnologia, che include tutti i controlli. Poiché potrebbe essere necessario individuare un controllo più volte durante un test, questo metodo offre al gestore della tecnologia un sistema per ottimizzare l'analisi delle proprietà di ricerca per il controllo specificato. Questo metodo restituisce inoltre un cookie che il framework può usare per le successive ricerche del controllo. Questa implementazione del metodo usa il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> per analizzare le proprietà di ricerca.  
  
## <a name="matchelement-method"></a>Metodo MatchElement  
 Per eseguire la ricerca di un controllo tramite il gestore della tecnologia, è possibile implementare il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> per restituire una matrice di possibili corrispondenze o generare l'eccezione <xref:System.NotSupportedException>, che indica al framework di usare il proprio algoritmo di ricerca. In entrambi i casi, è necessario implementare il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A>,per cui in questa implementazione viene nuovamente usato il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## <a name="navigation-methods"></a>Metodi per lo spostamento  
 Questi metodi ottengono gli elementi padre, figlio o di pari livello dell'elemento specificato dalla gerarchia dell'interfaccia utente. Il codice è semplice e commentato in modo chiaro.  
  
## <a name="getexcelelement-internal-method"></a>Metodo interno GetExcelElement  
 Questo metodo interno accetta un handle di finestra e informazioni su un elemento di Excel e restituisce l'elemento di Excel richiesto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
