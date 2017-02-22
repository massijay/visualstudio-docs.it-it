---
title: "Panoramica dell&#39;eliminazione nell&#39;origine | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "eliminazione origine, analisi codice"
  - "analisi codice, eliminazione origine"
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 40
caps.handback.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Panoramica dell&#39;eliminazione nell&#39;origine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'eliminazione nell'origine è la possibilità di eliminare o ignorare le violazioni rilevate dall'analisi del codice nel codice gestito tramite l'aggiunta dell'attributo **SuppressMessage** ai segmenti di codice che provocano le violazioni.  L'attributo **SuppressMessage** è un attributo condizionale incluso nei metadati IL dell'assembly del codice gestito solo se in fase di compilazione è stato definito il simbolo di compilazione CODE\_ANALYSIS.  
  
 In C\+\+C\+\+\/CLI, utilizzare le macro CA\_SUPPRESS\_MESSAGE o CA\_GLOBAL\_SUPPRESS\_MESSAGE nel file di intestazione per aggiungere l'attributo.  
  
 Non è consigliabile utilizzare eliminazioni nell'origine per le compilazioni di rilascio per impedire la definizione accidentale dei metadati di eliminazione nell'origine.  A causa dei costi di elaborazione dell'eliminazione nell'origine, le prestazioni dell'applicazione possono risultare ridotte se si includono i metadati di eliminazione nell'origine.  
  
> [!NOTE]
>  Non è necessario creare manualmente questi attributi.  Per ulteriori informazioni, vedere [Procedura: Eliminare gli avvisi tramite una voce di menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  La voce di menu non è disponibile per il codice C\+\+.  
  
## Attributo SuppressMessage  
 Facendo clic con il pulsante destro del mouse su un avviso dell'analisi del codice in **Elenco errori** e scegliendo **Elimina messaggi**, viene aggiunto un attributo **SuppressMessage** al codice o al file delle eliminazioni globali del progetto.  
  
 L'attributo **SuppressMessage** presenta il formato seguente:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```c#  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 \[C\+\+\]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Dove:  
  
-   **Rule Category**: la categoria in cui viene definita la regola.  Per ulteriori informazioni sulle categorie di regole di analisi del codice, vedere [Analisi del codice per gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Rule Id**: identificatore della regola.  Il supporto include sia un nome breve sia un nome lungo per l'identificatore della regola.  Il nome breve è CAXXXX, il nome lungo è CAXXXX:NomeTipoDescrittivo.  
  
-   **Justification**: il testo utilizzato per documentare il motivo dell'eliminazione del messaggio.  
  
-   **Message Id**: identificatore univoco di un problema per ciascun messaggio.  
  
-   **Scope**: la destinazione in cui è stato eliminato l'avviso.  Se la destinazione non è specificata, viene impostata sulla destinazione dell'attributo.  Gli ambiti supportati includono quanto segue:  
  
    -   Modulo  
  
    -   Spazio dei nomi  
  
    -   Risorsa  
  
    -   Type  
  
    -   Membro  
  
-   **Target**: identificatore utilizzato per specificare la destinazione in cui è stato eliminato l'avviso.  Deve contenere un nome completo dell'elemento.  
  
## Utilizzo di SuppressMessage  
 Gli avvisi dell'analisi del codice sono eliminati al livello a cui è applicata un'istanza dell'attributo **SuppressMessage** .  Lo scopo di questa procedura è quello creare un'associazione stretta tra le informazioni di eliminazione e il codice in cui si verifica la violazione.  
  
 La forma generale di eliminazione include la categoria della regola e un identificatore contenente una rappresentazione facoltativa leggibile del nome della regola.  Di seguito è riportato un esempio:  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 se la riduzione dei metadati dell'eliminazione nell'origine è strettamente legata alle prestazioni, il nome stesso della regola può essere omesso.  La categoria della regola e il relativo rule ID costituiscono insieme un identificatore della regola univoco e sufficiente.  Di seguito è riportato un esempio:  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Questo formato non è consigliato a causa dei problemi di gestibilità.  
  
## Eliminazione di più violazioni all'interno del corpo di un metodo  
 Gli attributi possono essere applicati solo a un metodo e non incorporati all'interno del corpo del metodo.  È tuttavia possibile specificare l'identificatore come ID messaggio per distinguere più occorrenze di una violazione all'interno di un metodo.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-cs[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## Codice generato  
 Compilatori del codice gestito e alcuni strumenti di terze parti generano codice per facilitare lo sviluppo rapido del codice.  Il codice generato dal compilatore visualizzato nei file sorgente è contrassegnato generalmente con l'attributo **GeneratedCodeAttribute**.  
  
 È possibile scegliere se eliminare gli avvisi e gli errori dell'analisi codice per il codice generato.  Per informazioni sull'eliminazione di tali avvisi ed errori, vedere [Procedura: eliminare gli avvisi per il codice generato](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 L'analisi codice ignora **GeneratedCodeAttribute** quando viene applicato a un intero assembly o a un solo parametro.  Queste situazioni si verificano raramente.  
  
## Eliminazioni a livello globale  
 Lo strumento di analisi del codice gestito esamina gli attributi **SuppressMessage** applicati a livello di assembly, modulo, tipo, membro o parametro.  Attiva inoltre le violazioni operate su risorse e spazi dei nomi.  Tali violazioni devono essere applicate a livello globale e vengono definite e destinate a un ambito.  Nel messaggio riportato di seguito, ad esempio, viene eliminata una violazione di uno spazio dei nomi.  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Quando si elimina un avviso il cui ambito è lo spazio dei nomi, viene eliminato l'avviso in base allo spazio dei nomi stesso.  L'avviso non viene eliminato in base ai tipi contenuti nello spazio dei nomi.  
  
 Qualsiasi eliminazione può essere espressa specificando un ambito esplicito.  Queste eliminazioni devono avvenire a livello globale.  Non è possibile specificare l'eliminazione a livello di membro mediante decorazione di un tipo.  
  
 Le eliminazioni a livello globale sono l'unico modo per eliminare messaggi che fanno riferimento a codice generato dal compilatore che non è associato a un'origine utente fornita esplicitamente.  Nel codice che segue, ad esempio, viene eliminata una violazione in base a un costruttore emesso dal compilatore:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  La destinazione contiene sempre il nome completo dell'elemento.  
  
## File di eliminazioni globali  
 Il file dell'eliminazione globale gestisce le eliminazioni a livello globale oppure le eliminazioni che non specificano una destinazione.  Le soppressioni per violazioni a livello di assembly, ad esempio, vengono archiviate in questo file.  Alcune eliminazioni ASP.NET, inoltre, vengono memorizzate in questo file in quanto le impostazioni a livello di progetto non sono disponibili per un modulo code\-behind.  Un'eliminazione globale viene creata e aggiunta al progetto la prima volta che si seleziona l'opzione **File di eliminazione in progetto** del comando **Elimina messaggi** nella finestra Elenco errori.  Per ulteriori informazioni, vedere [Procedura: Eliminare gli avvisi tramite una voce di menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## Vedere anche  
 <xref:System.Diagnostics.CodeAnalysis>