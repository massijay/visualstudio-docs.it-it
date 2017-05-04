---
title: "Elemento &lt;postActionData&gt; (sviluppo per Office in Visual Studio) | Microsoft Docs"
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
  - "elemento <postActionData>"
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <postActionData>"
  - "postActionData (elemento)"
ms.assetid: e36cbd64-fd27-4413-b293-cf5546fbdfaf
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Elemento &lt;postActionData&gt; (sviluppo per Office in Visual Studio)
  L'elemento `postActionData` dello spazio dei nomi `vstav3`  specifica i dati associati a qualsiasi azione post\-distribuzione che viene eseguita dopo l'installazione di soluzioni Office.  
  
## Sintassi  
  
```  
<postActionData>  
</postActionData>  
```  
  
## Elementi e attributi  
 L'elemento `postActionData` è facoltativo e si trova nello spazio dei nomi `vstav3` . Per ogni azione post\-distribuzione è definito un elemento `postActionData` in un manifesto dell'applicazione.  
  
 L'elemento `postActions` non ha attributi.  
  
 `postActions` è privo di elementi figlio.  
  
## Esempio di azione post\-distribuzione  
  
### Descrizione  
 L'esempio di codice seguente illustra l'elemento `postAction` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstav3:postActionData> data in any format </vstav3:postActionData>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  