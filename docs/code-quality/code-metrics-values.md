---
title: Valori della metrica del codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 234ec06d47afee3cbde7c2333742fe43ab599219
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="code-metrics-values"></a>Valori della metrica del codice
La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Sfruttando la metrica del codice, gli sviluppatori possono comprendere quali tipi e/o i metodi devono essere rielaborati oppure più approfonditi. I team di sviluppo possono identificare i potenziali rischi, comprendere lo stato corrente di un progetto e rilevare lo stato di avanzamento durante lo sviluppo di software.  
  
## <a name="software-measurements"></a>Misure del software  
 L'elenco seguente mostra i risultati della metrica codice [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Calcola:  
  
-   **Indice di manutenibilità** -calcola un valore di indice compreso tra 0 e 100 che rappresenta la relativa semplicità di gestione del codice. Un valore elevato indica una migliore gestibilità. Classificazioni codificato tramite colori consente di identificare rapidamente i punti critici del codice. Una classificazione verde è compreso tra 20 e 100 e indica che il codice ha una buona manutenibilità. Una classificazione gialla è compreso tra 10 e 19 e indica che il codice è moderatamente gestibile. Una classificazione rossa è compresa tra 0 e 9 e indica una manutenibilità insufficiente.  
  
-   **Complessità ciclomatica** -misura la complessità strutturale del codice. Viene creato per il calcolo del numero di percorsi del codice diversi nel flusso del programma. Un programma con il flusso di controllo complessi richiederà più test per ottenere un buon code coverage e sarà meno gestibile.  
  
    > [!NOTE]
    >  In alcuni casi, il calcolo della complessità ciclomatica di un metodo in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] differisce dalle versioni precedenti. Per ulteriori informazioni, vedere la sezione "modifiche in Visual Studio 2010 codice complessità calcoli" di [risoluzione dei problemi di metrica codice](../code-quality/troubleshooting-code-metrics-issues.md).  
  
-   **Profondità dell'ereditarietà** -indica il numero di definizioni di classi che estendono alla radice della gerarchia di classi. Maggiore è la profondità della gerarchia più difficile è possibile conoscere in cui vengono definiti determinati metodi e campi o / e ridefinito.  
  
-   **Accoppiamento** -misura l'accoppiamento di classi univoche tramite parametri, variabili locali, tipi restituiti, chiamate al metodo, creazioni di istanza generica o modello, le classi di base, le implementazioni dell'interfaccia, i campi definiti nei tipi esterni, e decorazione dell'attributo. Progettazione di software impone che i tipi e metodi devono avere coesione alta e accoppiamento basso. Accoppiamento elevato indica una progettazione che è difficile da riutilizzare e gestire a causa delle molte interdipendenze con altri tipi.  
  
-   **Righe di codice** -indica il numero approssimativo di righe di codice. Il conteggio è basato sul codice IL e pertanto non il numero esatto di righe nel file di codice sorgente. Un numero molto elevato potrebbe indicare che un tipo o metodo sta tentando di eseguire una quantità eccessiva di lavoro e deve essere suddiviso. Può inoltre indicare che il tipo o metodo potrebbe essere difficile da gestire.  
  
## <a name="anonymous-methods"></a>Metodi anonimi  
 Un *metodo anonimo* è semplicemente un metodo che non ha nome. Metodi anonimi vengono utilizzati principalmente per passare un blocco di codice come un parametro del delegato. Risultati di metrica per un metodo anonimo che viene dichiarato in un membro, ad esempio un metodo o una funzione di accesso, sono associati al membro che dichiara il metodo. Non sono associate con il membro che chiama il metodo.  
  
 Per ulteriori informazioni su come metrica del codice tratta i metodi anonimi, vedere [metodi anonimi e analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## <a name="generated-code"></a>Codice generato  
 Alcuni strumenti software e i compilatori di generano il codice che viene aggiunto a un progetto e che lo sviluppatore di progetto non consente di visualizzare o non deve modificare. In genere, la metrica del codice ignora il codice generato durante il calcolo dei valori delle metriche. In questo modo i valori della metrica in base a ciò che lo sviluppatore può visualizzare e modificare.  
  
 Codice generato per Windows Form non viene ignorato, poiché si tratta di codice che lo sviluppatore può visualizzare e modificare.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)