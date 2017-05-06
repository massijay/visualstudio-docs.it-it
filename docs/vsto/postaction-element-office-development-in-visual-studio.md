---
title: "Elemento &lt;postAction&gt; (sviluppo per Office in Visual Studio)"
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
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <postAction>"
  - "elemento <postAction>"
  - "postAction (elemento)"
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Elemento &lt;postAction&gt; (sviluppo per Office in Visual Studio)
  L'elemento `postAction` dello spazio dei nomi `vstav3`  contiene gli elementi `entrypoint` e tutti gli elementi `postActionData` associati alle azioni post\-distribuzione, che vengono eseguite dopo l'installazione delle soluzioni Office.  
  
## Sintassi  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## Elementi e attributi  
 L'elemento `postAction` è facoltativo e si trova nello spazio dei nomi `vstav3` . Per ogni azione post\-distribuzione è definito un elemento `postAction` in un manifesto dell'applicazione.  
  
 L'elemento `postAction` non ha attributi.  
  
 `postAction` presenta gli elementi seguenti:  
  
### entryPoint  
 Facoltativo. Il ruolo dell'elemento `entryPoint` nello spazio dei nomi `vstav3`  è definito in [Elemento &#60;entryPoints&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### postActionData  
 Facoltativo. Il ruolo dell'elemento `postActionData` nello spazio dei nomi `vstav3`  è definito in [Elemento &#60;postActionData&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).  
  
## Esempio di azione post\-distribuzione  
  
### Descrizione  
 L'esempio di codice seguente illustra l'elemento `postAction` in un manifesto dell'applicazione per una soluzione Office distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  