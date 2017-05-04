---
title: "Elemento &lt;customHostSpecified&gt; (sviluppo per Office in Visual Studio) | Microsoft Docs"
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
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <customHostSpecified>"
  - "<customHostSpecified> (elemento)"
  - "customHostSpecified (elemento)"
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Elemento &lt;customHostSpecified&gt; (sviluppo per Office in Visual Studio)
  L'elemento `customHostSpecified` indica che questa soluzione non è un'applicazione autonoma.  Le soluzioni Office contengono componenti che vengono ospitati in applicazioni Microsoft Office.  
  
## Sintassi  
  
```  
<customHostSpecified />  
```  
  
## Elementi e attributi  
 L'elemento `customHostSpecified` è obbligatorio per le soluzioni Office.  L'elemento si trova nello spazio dei nomi `co.v1` e specifica che questa distribuzione contiene un componente che sarà distribuito all'interno di un host personalizzato e non è un'applicazione autonoma.  
  
 È l'elemento figlio del primo elemento `<entrypoint>` nel manifesto dell'applicazione.  L'elemento `<entrypoint>` non può contenere altri elementi figlio altrimenti [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] genera un errore di convalida durante l'installazione.  
  
 Questo elemento non ha né attributi né figli.  
  
## Esempio  
 In l ' esempio di codice seguente viene illustrato l'elemento di `customHostSpecified` in un manifesto per un'applicazione per una soluzione Office.  Questo esempio di codice fa parte di un esempio più esaustivo fornito in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  