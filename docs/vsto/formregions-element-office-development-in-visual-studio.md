---
title: "Elemento &lt;formRegions&gt; (sviluppo per Office in Visual Studio)"
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
  - "formRegions (elemento)"
  - "elemento <formRegions>"
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <formRegions>"
ms.assetid: 71faa2da-9d38-43e8-9d7d-0bcd944ef9a3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Elemento &lt;formRegions&gt; (sviluppo per Office in Visual Studio)
  L'elemento `formRegions` dello spazio dei nomi `vstov4`  contiene le aree del modulo di Microsoft Office Outlook associate a un componente aggiuntivo VSTO.  
  
## Sintassi  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## Elementi e attributi  
 L'elemento `formRegions` dello spazio dei nomi `vstov4`  contiene tutti gli elementi `formRegion` per un componente aggiuntivo VSTO di Outlook. È obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo.  
  
 Può essere definito un solo elemento `formRegions` in un manifesto dell'applicazione.  
  
 L'elemento `formRegions` non ha attributi.  
  
 L'elemento `formRegions` presenta l'elemento seguente.  
  
### formRegion  
 Obbligatorio per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo. L'elemento `formRegion` viene definito in [Elemento &#60;formRegion&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## Esempio di componente aggiuntivo VSTO  
  
### Descrizione  
 L'esempio di codice seguente illustra un elemento `formRegions` in un manifesto dell'applicazione per una soluzione Office a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  