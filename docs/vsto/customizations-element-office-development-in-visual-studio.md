---
title: "Elemento &lt;customizations&gt; (sviluppo per Office in Visual Studio) | Microsoft Docs"
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
  - "elemento <customizations>"
  - "customizations (elemento)"
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <customizations>"
ms.assetid: fe1133ef-5fdf-4945-a67b-55a66a4e2109
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Elemento &lt;customizations&gt; (sviluppo per Office in Visual Studio)
  L'elemento `customizations` dello spazio dei nomi `vstov4` contiene tutte le informazioni sull'installazione e sul caricamento di ogni soluzione Office.  
  
## Sintassi per le personalizzazioni a livello di documento  
  
```  
<customizations> <customization id <document solutionId /> </customization> </customizations>  
```  
  
## Sintassi per i componenti aggiuntivi VSTO  
  
```  
<customizations> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </customizations>  
```  
  
## Elementi e attributi  
 L'elemento `customizations` contiene informazioni specifiche su ogni soluzione Office. Questo elemento deve essere presente nello spazio dei nomi seguente: `vstov4=urn:schemas-microsoft-com:vsto.v4`. In questo spazio dei nomi devono essere inclusi anche gli elementi figlio dell'assembly.  
  
 L'elemento `customizations` non ha attributi.  
  
 L'elemento `customizations` ha l'elemento figlio seguente.  
  
### personalizzazione  
 Obbligatorio. L'elemento `customization` nello spazio dei nomi `vstov4` è definito in [Elemento &#60;customization&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## Esempio di personalizzazione a livello di documento  
  
### Descrizione  
 L'esempio di codice seguente illustra l'elemento `customizations` per una personalizzazione a livello di documento.  
  
> [!NOTE]  
>  Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations>  
```  
  
## Esempio di componente aggiuntivo VSTO  
  
### Descrizione  
 L'esempio di codice seguente illustra l'elemento `customizations` per un componente aggiuntivo VSTO. Si tratta di un componente aggiuntivo VSTO per Outlook che include aree del modulo. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  