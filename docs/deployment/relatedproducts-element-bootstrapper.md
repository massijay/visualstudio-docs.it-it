---
title: "Elemento &lt;RelatedProducts&gt; (programma di avvio automatico) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<RelatedProducts> (elemento) [programma di avvio automatico]"
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;RelatedProducts&gt; (programma di avvio automatico)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento `RelatedProducts` definisce i prodotti inclusi nel prodotto corrente o che dipendono da quest'ultimo.  
  
## Sintassi  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## Elementi e attributi  
 L'elemento `RelatedProducts` è un elemento figlio di `Product`.  Non dispone di attributi.  
  
## DependsOnProduct  
 L'elemento `DependsOnProduct` indica che il prodotto corrente dipende dal prodotto specificato, che pertanto deve essere installato prima di quello corrente.  È un elemento figlio dell'elemento `RelatedProducts`.  Un elemento `RelatedProducts` può contenere uno o più elementi `DependsOnProduct`.  
  
 `DependsOnProduct` dispone dell'attributo riportato di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Code`|Nome del codice del prodotto incluso, specificato dall'attributo `ProductCode` dell'elemento `Product`.  Per ulteriori informazioni, vedere [Elemento \<Product\>](../deployment/product-element-bootstrapper.md).|  
  
## EitherProducts  
 L'elemento `EitherProducts` definisce zero o più elementi `DependsOnProduct` e non dispone di attributi.  Almeno un elemento `DependsOnProduct` in questo set deve essere installato prima del prodotto corrente.  Un elemento `RelatedProducts` può contenere zero o più elementi `EitherProducts`.  
  
## IncludesProduct  
 L'elemento `IncludesProduct` indica che un prodotto è incluso nell'installazione corrente e non richiede un'installazione separata.  È un elemento figlio dell'elemento `RelatedProducts`.  L'elemento `RelatedProducts` può contenere uno o più elementi `IncludesProduct`.  
  
 `IncludesProduct` dispone dell'attributo riportato di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Code`|Nome del codice del prodotto incluso, specificato dall'attributo `ProductCode` dell'elemento `Product`.  Per ulteriori informazioni, vedere [Elemento \<Product\>](../deployment/product-element-bootstrapper.md).|  
  
## Esempio  
 Nell'esempio di codice riportato di seguito è specificato che Microsoft Installer viene installato con [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e che pertanto non richiede un'installazione separata.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## Vedere anche  
 [Elemento \<Product\>](../deployment/product-element-bootstrapper.md)