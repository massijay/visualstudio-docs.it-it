---
title: "Elemento &lt;formRegion&gt; (sviluppo per Office in Visual Studio)"
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
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <formRegion>"
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Elemento &lt;formRegion&gt; (sviluppo per Office in Visual Studio)
  L'elemento `formRegion` dello spazio dei nomi `vstov4`  identifica un'area del modulo di Microsoft Office Outlook associata a un componente aggiuntivo VSTO.  
  
## Sintassi  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## Elementi e attributi  
 L'elemento `formRegion` dello spazio dei nomi `vstov4`  identifica un'area del modulo associata a un componente aggiuntivo VSTO di Outlook. È obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo.  
  
 Possono esserci più elementi `formRegion` definiti all'interno di un elemento `formRegions` per un componente aggiuntivo VSTO singolo.  
  
 L'elemento `formRegion` presenta l'attributo seguente:  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il nome dell'area del modulo.|  
  
 L'elemento `formRegion` ha gli elementi figlio seguenti.  
  
### messageClass  
 L'elemento `messageClass`  identifica il modulo di Outlook associato all'area del modulo.  
  
 L'elemento `messageClass` presenta l'attributo seguente:  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il modulo associato all'area del modulo.|  
  
## Esempio  
 L'esempio di codice seguente illustra un elemento `formRegion` in un manifesto dell'applicazione per un componente aggiuntivo VSTO di Outlook distribuito con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Esistono tre classi di messaggi associate a questa unica area del modulo. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion>  
```  
  
## Vedere anche  
 [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  