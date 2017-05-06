---
title: "Elemento &lt;application&gt; (sviluppo per Office in Visual Studio)"
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
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <application>"
ms.assetid: b8d3db7c-9127-4812-b18f-bb17e1f8788f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Elemento &lt;application&gt; (sviluppo per Office in Visual Studio)
  L'elemento `application` dello spazio dei nomi `vstav3` esegue il wrapping della descrizione delle soluzioni Office. Gli elementi figlio sono diversi per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
## Sintassi per le personalizzazioni a livello di documento  
  
```  
<application> <customization id <document solutionId /> </customization> </application>  
```  
  
## Sintassi per i componenti aggiuntivi a livello di applicazione  
  
```  
<application> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </application>  
```  
  
## Elementi e attributi  
 L'elemento `application` dello spazio dei nomi `vstav3` è il nodo che esegue il wrapping di tutte le informazioni specifiche delle personalizzazioni contenute nello spazio dei nomi `vstov4`.  
  
 L'elemento `application` non ha attributi.  
  
 L'elemento `application` presenta l'elemento seguente.  
  
### personalizzazione  
 Il ruolo dell'elemento `customization` nello spazio dei nomi `vstov3` è definito in [Elemento &#60;customization&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## Esempio di personalizzazione a livello di documento  
  
### Descrizione  
 L'esempio di codice seguente illustra un elemento `application` in una soluzione Office a livello di documento distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## Esempio di componente aggiuntivo VSTO  
  
### Descrizione  
 L'esempio di codice seguente illustra un elemento `application` in una soluzione Office a livello di applicazione distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  