---
title: "Procedura: Esportare uno shader | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 11
---
# Procedura: Esportare uno shader
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo documento viene illustrato come utilizzare la finestra di Progettazione shader per esportare uno shader nel linguaggio DGSL da utilizzare nella propria app.  
  
 In questo documento viene illustrata questa attività:  
  
-   Esportazione di uno shader  
  
## Esportazione di uno shader  
 Dopo avere creato uno shader tramite la finestra di Progettazione shader e prima di utilizzarlo nell'applicazione, è necessario esportarlo in un formato che gli API della grafica possono comprendere.  È possibile esportare uno shader in diversi modi per soddisfare esigenze differenti.  
  
#### Per esportare uno shader  
  
1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aprire un file **Visual Effect Graph \(.dgsl\)**.  
  
     Se non si dispone di un file **Visual Effect Graph \(.dgsl\)** da aprire, crearne uno come descritto in [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  Sulla barra degli strumenti **Progettazione shader**, scegliere **Avanzato**, **Esporta**, **Esporta come**.  Verrà visualizzata la finestra di dialogo **Esporta shader**.  
  
3.  Nell'elenco a discesa **Tipo file** scegliere il formato che si desidera esportare.  
  
     Di seguito sono riportati i formati che è possibile scegliere:  
  
     **Pixel Shader HLSL \(hlsl\)**  
     Esporta lo shader come codice sorgente High Level Shader Language \(HLSL\).  Questa opzione permette di modificare lo shader in un secondo momento, anche dopo che è stato distribuito in un'app.  Ciò può rendere più facile eseguire il debug e correggere il codice basato sui problemi dell'utente finale, ma rende più facile a un utente modificare lo shader in modi indesiderati, ad esempio per ottenere un vantaggio ingiusto in un gioco competitivo.  È inoltre possibile aumentare il tempo di caricamento dello shader.  
  
     **Pixel shader compilato \(\*.cso\)**  
     Esporta lo shader come bytecode HLSL.  Questa opzione permette di modificare lo shader in un secondo momento, anche dopo che è stato distribuito in un'app.  Ciò può rendere più facile eseguire il debug e correggere il codice sulla base dei problemi dell'utente finale, ma poiché lo shader è precompilato, non comporta un sovraccarico di runtime aggiuntivo quando lo shader viene caricato dall'applicazione.  Utenti sufficientemente esperti possono modificare lo shader in modalità indesiderate, ma compilare lo shader rende questo molto più complesso.  
  
     **Intestazione C\+\+ \(\*.h\)**  
     Esporta lo shader come intestazione di tipo C che definisce una matrice di byte contenente il bytecode HLSL.  Questa opzione può allungare i tempi di debug e correzione del codice basata sui problemi dell'utente finale poiché l'applicazione deve essere ricompilata per testare la correzione.  Questa opzione rende la modifica dello shader in seguito alla distribuzione in un'applicazione un'operazione difficile, sebbene non impossibile. Tuttavia, questa operazione è molto più difficile per un utente che desidera modificare lo shader in modalità non desiderate.  
  
4.  Nella casella combinata **Nome file** specificare un nome per lo shader esportato, quindi scegliere il pulsante **Salva**.  
  
## Vedere anche  
 [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md)   
 [Finestra di progettazione shader](../designers/shader-designer.md)