---
title: "Commenti e suggerimenti all&#39;utente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commenti e suggerimenti modello utente"
  - "contesto, ambiente"
  - "IDE, contesto"
  - "IDE, commenti degli utenti"
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Commenti e suggerimenti all&#39;utente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nell'ambiente di sviluppo integrato di \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , il feedback visivo per quanto riguarda funzionalità disponibili dipende dalla selezione corrente dell'utente e al contesto globale di selezione.  Nella seguente tabella sono elencate le funzionalità disponibile in contesti diversi di selezione.  
  
|contesto di selezione|funzionalità disponibile|  
|---------------------------|------------------------------|  
|IDE|Global|  
|Insieme corrente del prodotto|prodotto specifico|  
|gerarchia attiva|Tipo di struttura specifico|  
|Elemento attivo della gerarchia|Tipo di elemento della gerarchia specifico|  
|documento attivo|tipo di documento specifico|  
|Finestra in primo \(MDI\) piano con interfaccia a documenti multipli|Tipo di finestra specifico|  
|Il contesto della selezione corrente|contesto di selezione specifico|  
  
 Se sorgete solo il gli utenti necessitano di funzionalità e continuamente fornire la selezione coerente e il feedback di contesto dell'ambiente, si riduce la complessità dell'IDE.  Le regole seguenti si applicano ogni volta che una finestra è aperta nell'IDE:  
  
-   Se la finestra modificare il relativo contesto di selezione, il feedback di selezione viene illustrato dettagliatamente nella finestra e la finestra Guida dinamica, se visualizzata, viene aggiornata per riflettere il contesto corrente.  
  
-   Se la finestra cambia contesto globale di selezione, tutti i menu contesto\-specifici, la finestra attiva della gerarchia e la barra del titolo dell'applicazione vengono aggiornati per riflettere il contesto corrente.  
  
-   La finestra dovrebbe verificarsi le proprietà per la selezione corrente nella finestra di **Proprietà** e facoltativamente, se visualizzata, la finestra di dialogo di **Pagine delle proprietà** .  
  
-   Se la finestra non viene visualizzato le proprietà o non cambia contesto globale di selezione, il feedback di selezione non deve rimanere nella finestra quando non è più la finestra attiva nell'IDE.  
  
-   Tutte le finestre degli strumenti documento\-specifiche devono riflettere sempre il documento attivo.  
  
-   I menu, barre degli strumenti e la barra del titolo dell'applicazione devono riflettere la finestra in primo piano client MDI \(MDI\).  
  
 Ad esempio, quando la visualizzazione HTML di un Web Form in un progetto di applicazione Web Visual Basic è aperta e l'utente seleziona un tag di `<td>` , il feedback viene fornito nel modo seguente:  
  
-   La selezione viene visualizzata nella finestra attiva e viene riportata nella finestra di **Proprietà** .  
  
-   **Casella degli strumenti** documento\-specifico aggiornato per riflettere il documento attivo.  
  
-   La barra degli strumenti di **editor** e il menu di **Tabella** visualizzare e gli aggiornamenti della didascalia per riflettere la finestra Web Form.  
  
-   La finestra attiva della gerarchia, che in genere **Esplora soluzioni**e il relativo aggiornamento della didascalia per riflettere il contesto corrente e i comandi di menu sensibili al contesto di **Progetto** ora si applicano al progetto di applicazione Web attivo.  
  
## Vedere anche  
 [Selezione e la valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md)   
 [Selezione e gerarchie](../../extensibility/internals/hierarchies-and-selection.md)