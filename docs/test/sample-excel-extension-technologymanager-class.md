---
title: "Estensione Excel di esempio: classe TechnologyManager | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Estensione Excel di esempio: classe TechnologyManager
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa classe estende la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> ed è responsabile per la fornitura di servizi di base per l'estensione [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  Anche se la classe base dispone di molti metodi, solo un sottoinsieme di questi viene utilizzato in questo esempio.  
  
 Alcuni metodi restituiscono solo un valore della proprietà.  Molti dei metodi devono consentire allo sviluppatore di eseguire l'override di algoritmi predefiniti incorporati nel motore del test codificato dell'interfaccia utente.  Questi metodi generano un oggetto <xref:System.NotSupportedException> o restituiscono `null`, il che indica al framework di utilizzare l'algoritmo predefinito.  
  
 A seconda della complessità della tecnologia sottostante, lo sviluppo del codice del gestore tecnologia potrebbe richiedere da alcune settimane ad alcuni mesi.  Excel fornisce l'opportunità di creare un gestore tecnologia potenzialmente molto esteso.  Questo esempio è limitato intenzionalmente a fogli di lavoro e celle di Excel e utilizza una formattazione limitata.  
  
 Quando è possibile, il codice del gestore tecnologia utilizza il canale .NET Remoting aperto dalla classe `Communicator` per estrarre informazioni dal componente aggiuntivo in esecuzione nel processo di Excel.  
  
## Visibilità COM  
 Si noti che questa classe e ciascuna delle classi di elementi che estendono la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> dispongono tutte dell'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> con un valore di `true` per garantire che le classi siano visibili a COM.  
  
## Proprietà TechnologyName  
 Questo override della proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> deve fornire un nome univoco e significativo che identifichi la tecnologia sottostante per tutti gli altri componenti dell'estensione.  Per questa estensione, il valore è "Excel".  
  
## Metodo GetControlSupportLevel  
 Questo override del metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> restituisce un numero che indica il livello di supporto che il gestore tecnologia può offrire per il controllo rappresentato dall'handle fornito.  Quanto più elevato il valore restituito, più il gestore tecnologia sarà in grado di supportare il controllo.  In questo caso, il metodo controlla la finestra che contiene il controllo e, se è un Foglio di lavoro di Excel, il metodo restituisce il valore massimo; in caso contrario, restituisce zero, che indica che non è fornito alcun supporto.  
  
## Metodi per ottenere un elemento  
 Sono disponibili molti metodi importanti utilizzati dal framework dei test codificati dell'interfaccia utente per ottenere un elemento specifico della tecnologia mediante un handle, un punto nello schermo o un elemento da una tecnologia diversa.  Il codice per questi metodi è di facile comprensione.  Di seguito sono descritti i metodi di base:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## Metodo ParseQueryId  
 Quando viene creato un test codificato dell'interfaccia utente, l'utente può specificare valori di proprietà per alcuni o per tutti i controlli nel test.  Tali valori di proprietà vengono utilizzati dal framework di test per creare coppie nome\/valore, denominate proprietà di ricerca, utilizzate per trovare controlli dell'interfaccia utente specifici nel corso del test.  Tutte le proprietà di ricerca rappresentano insieme il valore della proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> di ogni elemento nella tecnologia che include ciascun controllo.  Poiché un controllo potrebbe dover essere trovato molte volte durante un test, questo metodo fornisce al gestore tecnologia un modo per ottimizzare l'analisi delle proprietà di ricerca per il controllo specificato.  Questo metodo restituisce anche un cookie che il framework può utilizzare per ricerche successive relative a quel controllo.  Questa implementazione del metodo utilizza il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> per analizzare le proprietà di ricerca.  
  
## Metodo MatchElement  
 Per eseguire una ricerca di controlli dal gestore tecnologia, è possibile implementare il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> per restituire una matrice di possibili corrispondenze oppure generare l'eccezione <xref:System.NotSupportedException>che indica al framework di utilizzare il proprio algoritmo di ricerca.  In ogni caso, è necessario implementare il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> laddove questa implementazione utilizzi nuovamente il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## Metodi di navigazione  
 Questi metodi ottengono l'elemento padre, gli elementi figlio o elementi di pari livello dell'elemento fornito dalla gerarchia di interfacce utente.  Il codice è semplice e commentato in modo chiaro.  
  
## Metodo interno GetExcelElement  
 Questo metodo interno ottiene un handle di finestra e informazioni su un elemento Excel, quindi restituisce l'elemento Excel richiesto.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)