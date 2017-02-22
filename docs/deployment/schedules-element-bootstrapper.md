---
title: "Elemento &lt;Schedules&gt; (programma di avvio automatico) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Schedules> (elemento) [programma di avvio automatico]"
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;Schedules&gt; (programma di avvio automatico)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento `Schedules` contiene gli elementi `Schedule`, che definiscono l'ora specifica in cui eseguire i comandi specificati dall'elemento `Command`.  
  
## Sintassi  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## Elementi e attributi  
 L'elemento `Schedules` è un elemento figlio di `Product`.  Ciascun elemento `Product` può contenere al massimo un elemento `Schedules`.  L'elemento `Schedules` non contiene attributi.  
  
## Schedule  
 L'elemento `Schedule` è un elemento figlio di `Schedules`.  Un elemento `Schedules` deve contenere almeno un elemento `Schedule`.  
  
 `Schedule` dispone dell'attributo riportato di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio.  Nome dell'elemento di pianificazione.  Questo parametro corrisponde alla proprietà `ScheduleName` dell'elemento `Command`.  Quando un elemento `Command` fa riferimento alla pianificazione specificata, tale elemento verrà eseguito soltanto nel momento indicato dall'elemento `Schedule`.  Le pianificazioni possono anche essere associate agli elementi `FailIf` e `BypassIf`, che limitano l'esecuzione dei test condizionali nella pianificazione specificata.  Per ulteriori informazioni, vedere [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
  
 Un determinato elemento `Schedule` può avere esattamente uno degli elementi figlio riportati di seguito.  
  
## BuildList  
 L'elemento `BuildList` indica al programma di installazione di eseguire un comando immediatamente dopo l'avvio dell'applicazione di avvio automatico.  
  
## BeforePackage  
 L'elemento `BeforePackage` indica al programma di installazione di eseguire un comando prima dell'installazione del package specificato.  
  
## AfterPackage  
 L'elemento `AfterPackage` indica al programma di installazione di eseguire un comando dopo l'installazione del package specificato.  
  
## Vedere anche  
 [Elemento \<Product\>](../deployment/product-element-bootstrapper.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)