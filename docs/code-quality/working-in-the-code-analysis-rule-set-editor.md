---
title: "Utilizzo dell&#39;editor set di regole di analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.ruleseteditor"
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Utilizzo dell&#39;editor set di regole di analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor set di regole di analisi del codice consente di specificare le regole incluse in un set di regole personalizzato e di specificare l'azione.  È inoltre possibile specificare l'azione da eseguire quando l'analisi del codice rileva una violazione della regola.  
  
|Azione|Descrizione|  
|------------|-----------------|  
|**Warning**|Genera un avviso nella finestra **Elenco errori**.|  
|**Error**|Genera un errore nella finestra **Elenco errori**.|  
|**None**|Disabilita la regola.|  
  
 Le regole vengono visualizzate in una struttura ad albero raggruppate in base a un campo specificato.  Per aggiungere o rimuovere regole da un set di regole, effettuare uno o più dei passaggi seguenti:  
  
-   Selezionare o deselezionare la casella di controllo del nodo gruppo per aggiungere o rimuovere tutte le regole del gruppo.  Quando si seleziona un gruppo, tutte le regole vengono impostate sull'azione **Avviso**.  
  
-   Fare clic sul campo **Azione** di un gruppo, quindi specificare l'azione da applicare a tutte le regole del gruppo.  
  
-   Selezionare o deselezionare la casella di controllo per una singola regola.  Quando si seleziona la casella di controllo per una regola, quest'ultima viene impostata sull'azione Avviso.  
  
## Barra degli strumenti dell'editor set di regole  
 È possibile utilizzare la barra degli strumenti dell'editor set di regole per raggruppare, filtrare e cercare i dati visibili nella griglia del set di regole.  
  
 Nella tabella seguente vengono descritti i controlli della barra degli strumenti dell'editor set di regole.  
  
|Controllo della barra degli strumenti|Descrizione|  
|-------------------------------------------|-----------------|  
|**Espandi tutto**|Mostra le regole di tutti i gruppi.|  
|**Comprimi tutto**|Nasconde le regole di tutti i gruppi.|  
|**Group By**|Specifica il campo in base al quale vengono raggruppate le regole.  Fare clic **\<Nessuno\>** per mostrare le regole senza gruppi.|  
|**Opzioni colonna**|Specifica i campi delle regole da visualizzare.|  
|**Nascondi le regole che non si applicano alla soluzione corrente**|Mostra o nasconde le regole che non sono dello stesso tipo di destinazione della soluzione.|  
|**Mostra regole che possono generare errori di analisi codice**|Mostra o nasconde le regole a cui è stata assegnata l'azione Errore.|  
|**Mostra regole che possono generare errori di analisi codice**|Mostra o nasconde le regole a cui è stata assegnata l'azione di avviso.|  
|**Mostra regole non abilitate**|Mostra o nasconde le regole a cui è stata assegnata l'azione Nessuna.|  
|**Aggiungi o rimuovi set di regole figlio**|Aggiunge o rimuove le regole nei set di regole selezionati.|  
|**Cerca regole**|Cerca la stringa specificata in tutti i valori dei campi.|  
  
## Campi set di regole  
 I campi del set di regole contengono informazioni su un set di regole e possono essere utilizzati per ordinare e raggruppare l'elenco delle regole.  Per visualizzare o nascondere campi, fare clic su **Opzioni colonne** sulla barra degli strumenti dell'editor set di regole, quindi selezionare o deselezionare le caselle di controllo dei campi da mostrare o nascondere.  
  
 Nella tabella seguente vengono descritti i campi di un set di regole.  
  
|Campo|Descrizione|  
|-----------|-----------------|  
|**ID**|Identificatore della regola.|  
|**Category**|Le regole di analisi del codice vengono raggruppate per categoria e per appartenenza ai set di regole.  Per ulteriori informazioni, vedere [Analisi del codice per gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|Titolo della regola.|  
|**Namespace**|Spazio dei nomi della regola.|  
|**Target Type**|Indica se la regola è destinata a codice nativo, gestito o del database.|  
|**Action**|L'azione eseguita quando la regola viene violata in un'esecuzione di analisi codice.<br /><br /> **Warning**: genera un avviso.<br /><br /> **Error**: genera un errore.<br /><br /> **None**: disabilita la regola.<br /><br /> È possibile modificare il campo Azione.  Impostare il valore su Nessuno equivale a deselezionare la casella di controllo per la regola.|  
|**Source Rule Sets**|Set di regole che contiene la regola.|  
  
## Ordinamento e filtro dei set di regole  
 È possibile ordinare e filtrare le regole in base ai valori del campo utilizzando le intestazioni di colonna della griglia dei set di regole.  
  
-   Per ordinare gli elenchi di set di regole, fare clic sull'intestazione di colonna del campo su cui si desidera basare l'ordinamento.  Se i set di regole sono raggruppati, ogni gruppo viene ordinato singolarmente.  
  
-   Per filtrare i set di regole in base al valore di un campo, fare clic sul pulsante filtro nell'intestazione di colonna del campo su cui si desidera basare il filtro.  Selezionare le caselle di controllo dei valori che si desidera mostrare e deselezionare quelle dei valori che si desidera nascondere.