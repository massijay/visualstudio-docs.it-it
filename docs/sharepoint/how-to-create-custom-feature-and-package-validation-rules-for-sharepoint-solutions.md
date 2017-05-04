---
title: "How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending deployment"
  - "SharePoint development in Visual Studio, validation rules"
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions
  È possibile creare regole di convalida personalizzate per verificare il pacchetto di soluzione generato in Visual Studio.  Per eseguire la convalida completa di un'intera funzionalità o di un intero pacchetto, scegliere **Convalida** dal menu di scelta rapida di un pacchetto o di una funzionalità in **Esplorapacchetti**.  La convalida parziale viene eseguita quando si aggiungono nuovi elementi di progetto SharePoint o nuove funzionalità al progetto, allo scopo di determinare se il pacchetto o la funzionalità ha uno stato valido.  
  
### Per creare una regola di convalida personalizzata per un pacchetto  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Crea una classe che implementa una delle interfacce seguenti:  
  
    -   Per creare una regola di convalida per un pacchetto, implementare l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>.  
  
    -   Per creare una regola di convalida per una funzionalità, implementare l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>.  
  
4.  Aggiungere l'oggetto <xref:System.ComponentModel.Composition.ExportAttribute> alla classe.  Questo attributo consente a Visual Studio di individuare e caricare la regola di convalida.  Passare il tipo <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> o <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> al costruttore dell'attributo.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come creare una regola di convalida personalizzata per una funzionalità.  
  
 [!code-csharp[SPExtensibility.FeatureValidation#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.featurevalidation/cs/extension/customfeaturevalidationrule.cs#1)]
 [!code-vb[SPExtensibility.FeatureValidation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.featurevalidation/vb/extension/customvalidationrule.vb#1)]  
  
## Compilazione del codice  
 In questo esempio sono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  