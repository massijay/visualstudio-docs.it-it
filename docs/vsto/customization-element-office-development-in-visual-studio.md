---
title: "Elemento &lt;customization&gt; (sviluppo per Office in Visual Studio)"
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
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <customization>"
ms.assetid: a3bf7f35-bd98-4530-9226-46489cd37bb1
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Elemento &lt;customization&gt; (sviluppo per Office in Visual Studio)
  L'elemento `customization` dello spazio dei nomi `vstov4` descrive una specifica soluzione Office. Gli elementi figlio sono diversi per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
## Sintassi per le personalizzazioni a livello di documento  
  
```  
<customization id <document solutionId /> </customization>  
```  
  
## Sintassi per i componenti aggiuntivi VSTO  
  
```  
<customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization>  
```  
  
## Elementi e attributi  
 L'elemento `customization` contiene informazioni specifiche della personalizzazione. Questo elemento deve essere presente nello spazio dei nomi seguente: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Esiste un elemento `customization` per ogni soluzione Office. Ad esempio, se si distribuiscono tre soluzioni Office in una distribuzione multiprogetto, nel manifesto dell'applicazione sono presenti tre elementi `customization`.  
  
 In questo spazio dei nomi devono essere inclusi anche gli elementi figlio dell'assembly.  
  
 L'elemento `customization` presenta l'attributo seguente:  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`id`|Necessario per la distribuzione multiprogetto. L'elemento `id` identifica in modo univoco una soluzione Office.|  
  
### Personalizzazioni a livello di documento  
 L'elemento `customization` ha l'elemento figlio seguente.  
  
#### documento  
 L'elemento `document` nello spazio dei nomi `vstov4` è definito in [Elemento &#60;document&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).  
  
### Componenti aggiuntivi VSTO  
 L'elemento `customization` ha l'elemento figlio seguente.  
  
#### appAddin  
 L'elemento `appAddin` nello spazio dei nomi `vstov4` è definito in [Elemento &#60;appAddin&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).  
  
## Esempio di personalizzazione a livello di documento  
  
### Descrizione  
 L'esempio di codice seguente illustra l'elemento `customization` per una personalizzazione a livello di documento. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization>  
```  
  
## Esempio di componente aggiuntivo VSTO  
  
### Descrizione  
 L'esempio di codice seguente illustra l'elemento `customization` per un componente aggiuntivo VSTO. Si tratta di un componente aggiuntivo VSTO per Outlook che include aree del modulo. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  