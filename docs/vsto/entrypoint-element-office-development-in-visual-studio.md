---
title: "Elemento &lt;entryPoint&gt; (sviluppo per Office in Visual Studio) | Microsoft Docs"
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
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <entryPoint>"
  - "elemento <entryPoint>"
  - "entryPoint (elemento)"
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Elemento &lt;entryPoint&gt; (sviluppo per Office in Visual Studio)
  Ogni elemento `entryPoint` dello spazio dei nomi `vstav3` identifica un assembly di personalizzazione che deve essere eseguito quando l'applicazione[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] è installata.  
  
## Sintassi  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## Elementi e attributi  
 L'elemento `entryPoint` è obbligatorio e si trova nello spazio dei nomi `vstav3` .  
  
 Ogni elemento `entryPoint` può contenere solo un assembly di personalizzazione. Possono essere definiti più elementi `entryPoint` in un manifesto dell'applicazione.  
  
 L'elemento `entryPoint` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`class`|Obbligatorio. Identifica un assembly di personalizzazione da eseguire. La sintassi per questo attributo è *NamespaceName.ClassName*.|  
  
 `entryPoint` presenta l'elemento seguente:  
  
### assemblyIdentity  
 Obbligatorio. L'elemento `assemblyIdentity` nello spazio dei nomi `vstav3` si riferisce a un elemento `assemblyIdentity` esistente nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  
  
 Il ruolo di `assemblyIdentity` e i relativi attributi sono definiti in [&#60;assemblyIdentity&#62; Element &#40;ClickOnce Application&#41;](~/deployment/assemblyidentity-element-clickonce-application.md).  
  
## Esempio di personalizzazione a livello di documento  
  
### Descrizione  
 L'esempio di codice seguente illustra elementi `entryPoint` in un manifesto dell'applicazione per una soluzione Office a livello di documento distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## Esempio di componente aggiuntivo VSTO  
  
### Descrizione  
 L'esempio di codice seguente illustra un elemento `entryPoint` in un manifesto dell'applicazione per una soluzione Office a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## Vedere anche  
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  