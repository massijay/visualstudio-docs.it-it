---
title: "Elemento &lt;postActions&gt; (sviluppo per Office in Visual Studio)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <postActions>"
  - "postActions (elemento)"
  - "elemento <postActions>"
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Elemento &lt;postActions&gt; (sviluppo per Office in Visual Studio)
  L'elemento `postActions` dello spazio dei nomi `vstav3`  contiene tutti gli elementi `postAction` che descrivono le azioni post\-distribuzione, che vengono eseguite dopo l'installazione delle soluzioni Office.  
  
## Sintassi  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## Elementi e attributi  
 L'elemento `postActions` è facoltativo e si trova nello spazio dei nomi `vstav3` . Viene definito un solo elemento `postActions` in un manifesto dell'applicazione.  
  
 L'elemento `postActions` non ha attributi.  
  
 `postActions` presenta l'elemento seguente:  
  
### postAction  
 Facoltativo. Il ruolo dell'elemento `postAction` nello spazio dei nomi `vstav3`  è definito in [Elemento &#60;postAction&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## Esempio di azione post\-distribuzione  
  
### Descrizione  
 L'esempio di codice seguente illustra l'elemento `postActions` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstav3:postActions> <vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction> </vstav3:postActions>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  