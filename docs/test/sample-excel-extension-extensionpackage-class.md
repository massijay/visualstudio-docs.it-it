---
title: "Estensione Excel di esempio: classe ExtensionPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Estensione Excel di esempio: classe ExtensionPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa classe estende la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> e fornisce il punto di ingresso per un test codificato dell'interfaccia utente che sta testando un Foglio di lavoro di [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## Attributo dell'assembly  
 Il file inizia con un attributo dell'assembly che identifica l'assembly come estensione di test dell'interfaccia utente.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 L'attributo dichiara il nome della classe base, il nome della classe del pacchetto e il nome di classe completo per la classe del pacchetto di estensione personalizzata.  
  
## Proprietà semplici  
 Tale classe dispone di proprietà che forniscono valori utilizzati dal framework dei test codificati dell'interfaccia utente per identificare e descrivere l'estensione e l'assembly.  Per ulteriori informazioni, vedere i commenti del codice.  
  
## Metodo GetService  
 Il metodo <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> è il singolo punto di ingresso utilizzato dal framework dei test codificati dell'interfaccia utente per accedere al gestore tecnologia, al provider delle proprietà nonché al filtro azioni, come identificato dalla classe di base per ciascun oggetto.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)