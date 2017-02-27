---
title: "Procedura dettagliata: Configurazione e uso di un set di regole personalizzate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analisi codice, procedure dettagliate"
  - "analisi codice, set di regole"
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 40
---
# Procedura dettagliata: Configurazione e uso di un set di regole personalizzate
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come utilizzare gli strumenti di analisi del codice configurati per l'utilizzo di un *set di regole* personalizzato su una libreria di classi.  È possibile selezionare un set di regole correlato al tipo di progetto specificato per la soluzione oppure è possibile selezionare set di regole alternativi per soddisfare esigenze specifiche quali l'analisi del codice legacy per individuare problemi che possono essere corretti senza bisogno di apportare modifiche sostanziali.  In entrambi i casi, è possibile personalizzare i set di regole per adattarli al meglio ai requisiti del progetto.  
  
 In questa procedura dettagliata verranno esaminati i processi seguenti:  
  
-   Creare una libreria di classi.  
  
-   Selezionare il set di regole di analisi del codice **Regole base delle linee guida di progettazione Microsoft**.  
  
-   Aggiungere codice personalizzato alla classe.  
  
-   Eseguire l'analisi del codice.  
  
-   Personalizzare il set di regole.  
  
-   Eseguire l'analisi del codice ed esaminare il comportamento delle personalizzazioni del set di regole.  
  
## Prerequisiti  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## Utilizzo di set di regole con l'analisi del codice  
 Creare innanzitutto una semplice libreria di classi.  
  
#### Creare una libreria di classi  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** fare clic su **Visual C\#** in **Tipi di progetto**.  
  
3.  In **Visual C\#** selezionare **Libreria di classi**.  
  
4.  Nella casella di testo **Nome** digitare RuleSetSample e fare clic su **OK**.  
  
 A questo punto, è possibile selezionare il set di regole **Regole base delle linee guida di progettazione Microsoft** e salvarlo con il progetto.  
  
#### Selezionare un set di regole di analisi codice  
  
1.  Scegliere **Configura analisi codice per RuleSetSample** dal menu **Analizza**.  
  
     Verranno visualizzate le impostazioni di configurazione dell'analisi del codice.  
  
2.  Nell'elenco a discesa **Esegui il set di regole** selezionare **Tutte le regole Microsoft**.  
  
     Per ulteriori informazioni sui set di regole disponibili, vedere [Tabella di riferimento del set di regole di analisi del codice](../code-quality/code-analysis-rule-set-reference.md).  
  
     Scegliere **Salva elementi selezionati** dal menu File per aggiornare il file di progetto con le informazioni sul set di regole selezionato e le relative impostazioni.  
  
    > [!TIP]
    >  In situazioni reali, è consigliabile assegnare priorità ai problemi per i quali si esegue l'analisi codice iniziando con il set di regole **Regole minime consigliate** per correggere i problemi desiderati e aggiungendo progressivamente altre regole o altri set di regole per individuare e correggere ulteriori problemi.  
  
 A questo punto, è possibile procedere all'aggiunta alla libreria di classi di codice da utilizzare per evidenziare le violazioni della regola di analisi codice CA1804 Gli identificatori devono essere digitati correttamente".  Per ulteriori informazioni, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### Aggiungere codice personalizzato  
  
-   In Esplora soluzioni aprire il file Class1.cs e sostituire il codice esistente con quello che segue:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }  
  
    ```  
  
 È ora possibile eseguire l'analisi del codice sul progetto RuleSetSample e cercare eventuali errori e avvisi generati nella finestra Elenco errori.  
  
#### Eseguire l’analisi codice sul progetto RuleSetSample  
  
1.  Scegliere **Esegui analisi del codice su RuleSetSample** dal menu **Analizza**.  
  
2.  Nella finestra Elenco errori fare clic su **Avvisi**, quindi sull'intestazione di colonna **Descrizione** per disporre gli avvisi in ordine alfanumerico.  
  
     In un'applicazione reale, si procederebbe a questo punto alla correzione di eventuali violazioni delle regole che è opportuno risolvere oppure, nel caso in cui la correzione risulti irrilevante, alla disabilitazione della regola corrispondente.  Per ulteriori informazioni, vedere [Rimuovere avvisi tramite l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3.  Si notino gli avvisi CA1704.  Tali violazioni di questa regola indicano che è necessario "fornire un più nome significativo per i parametri". È possibile correggere il problema nel codice o disabilitare la regola, come illustrato nella procedura successiva.  
  
 Si personalizzerà quindi il set di regole in modo da escludere l'avviso CA1704 "Gli identificatori devono essere digitati correttamente".  
  
#### Personalizzare il set di regole per il progetto in modo da disabilitare una regola specifica  
  
1.  Scegliere **Configura analisi codice per RuleSetSample** dal menu **Analizza**.  
  
2.  Nell'elenco a discesa **Esegui il set di regole**, verificare che il set di regole **Tutte le regole Microsoft** sia ancora evidenziato, quindi fare clic su **Apri**.  Verrà visualizzata la pagina del set di regole.  
  
3.  Espandere il nodo della categoria Microsoft.Naming, quindi selezionare l'avviso CA1704.  
  
4.  Nella colonna **Azione** selezionare **Nessuna**. Ciò impedisce la visualizzazione di avvisi o errori relativi alla regola CA1704 nella finestra Elenco errori.  
  
     In questa fase, è consigliabile provare i diversi pulsanti della barra degli strumenti e le opzioni di filtro allo scopo di acquisire familiarità con il prodotto.  È ad esempio possibile utilizzare l'elenco a discesa **Raggruppa per** per agevolare l'individuazione di una regola o di una categoria di regole specifica.  È inoltre possibile, ad esempio, utilizzare il pulsante **Nascondi regole disabilitate** sulla barra degli strumenti delle pagine del set di regole per nascondere o visualizzare tutte le regole con la colonna **Azione** impostata su **Nessuna**.  Ciò può risultare utile se si desidera cercare eventuali regole disabilitate per determinare se sia opportuno abilitarle o meno.  
  
5.  Scegliere Finestra Proprietà dal menu Visualizza.  Digitare **My Custom Rule Set** nella casella Nome della finestra degli strumenti Proprietà.  Il nome visualizzato del nuovo set di regole verrà modificato nell'IDE di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
6.  Scegliere **Salva** dal menu **File** per salvare il set di regole personalizzate.  Passare alla cartella radice del progetto.  Nella casella di testo **Nome file** digitare SetRegolePersonalizzato.  Il set di regole personalizzato può ora essere selezionato per l'utilizzo con il progetto.  
  
 Dopo aver creato il nuovo set di regole, è necessario configurare le impostazioni del progetto per specificare che si desidera utilizzare tale set di regole.  
  
#### Specificare il nuovo set di regole da utilizzare con il progetto  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.  
  
2.  Nella scheda **Proprietà** fare clic su **Analisi codice**.  
  
     Nell'elenco a discesa **Esegui il set di regole** fare clic su **\<Sfoglia...\>**.  Passare alla cartella radice del progetto di codice e quindi selezionare SetRegolePersonalizzato.ruleset.  Si tratta del nuovo set di regole creato nella procedura precedente.  
  
3.  Scegliere **Salva** dal menu **File** per salvare la configurazione del progetto.  Il set di regole personalizzato può ora essere utilizzato con il progetto.  
  
 È infine possibile eseguire di nuovo l'analisi del codice con il set di regole SetRegolePersonalizzato.  Si noti che nella finestra Elenco errori non viene visualizzata la violazione della regola di prestazioni CA1704.  
  
#### Eseguire l'analisi codice sul progetto RuleSetSample per la seconda volta  
  
1.  Scegliere **Esegui analisi del codice su RuleSetSample** dal menu **Analizza**.  
  
2.  Nella finestra Elenco errori, si noti che facendo clic su **Avvisi** non vengono più visualizzati gli avvisi di violazione CA1704 per la regola "Gli identificatori devono essere digitati correttamente".  
  
## Vedere anche  
 [Procedura: Configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Tabella di riferimento del set di regole di analisi del codice](../code-quality/code-analysis-rule-set-reference.md)