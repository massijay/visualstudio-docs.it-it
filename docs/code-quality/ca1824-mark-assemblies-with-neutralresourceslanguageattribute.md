---
title: "CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1824"
  - "MarkAssembliesWithNeutralResourcesLanguage"
helpviewer_keywords: 
  - "MarkAssembliesWithNeutralResourcesLanguage"
  - "CA1824"
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1824: Contrassegnare gli assembly con NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|CheckId|CA1824|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un assembly contiene una risorsa basata su **ResX**, ma è privo di un attributo <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>.  
  
## Descrizione della regola  
 L'attributo **NeutralResourcesLanguage** indica a **ResourceManager** il linguaggio utilizzato per visualizzare le risorse delle impostazioni cultura non associate ad alcun paese per un assembly.  Durante la ricerca di risorse con le stesse impostazioni cultura utilizzate per la lingua risorse neutra, **ResourceManager** utilizza automaticamente le risorse contenute nell'assembly principale,  Viene eseguita questa operazione anziché cercare un assembly satellite con le impostazioni cultura dell'interfaccia corrente per il thread corrente.  Tale approccio migliora le prestazioni delle ricerche per la prima risorsa caricata e riduce il working set.  
  
## Correzione di violazioni  
 Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly e specificare il linguaggio delle risorse delle impostazioni cultura non associate ad alcun paese.  
  
## Impostazione della lingua  
  
#### Per specificare la lingua della risorsa delle impostazioni cultura non associate ad alcun paese  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.  
  
2.  Utilizzando la barra di navigazione sinistra selezionare **Applicazione**, quindi fare clic su **Informazioni assembly**.  
  
3.  Nella finestra di dialogo **Informazioni assembly** selezionare la lingua dall'elenco a discesa **Lingua di sistema**.  
  
4.  Fare clic su **OK**.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è consentita.  Le prestazioni all'avvio potrebbero tuttavia diminuire.