---
title: Modellare i requisiti dell&quot;utente | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- requirements
- stories
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 28
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 08aabdfe0e268f93ef7723076375b7f65b15ccf3
ms.openlocfilehash: 60866c46920bb85927498992082763f9e34b4137
ms.lasthandoff: 02/22/2017

---
# <a name="model-user-requirements"></a>Modellare i requisiti utente
Visual Studio facilita la comprensione, la discussione e la comunicazione delle esigenze degli utenti mediante la creazione di diagrammi delle attività e del ruolo che il sistema svolge per il raggiungimento degli obiettivi. Un modello di requisiti è un set di tali diagrammi, ognuno dei quali è incentrato su un aspetto diverso delle esigenze degli utenti. Per una dimostrazione video, vedere: [Modellazione del dominio aziendale](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/).  
  
 Per informazioni sulle versioni di Visual Studio supportano ogni tipo di modello, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Un modello di requisiti consente di:  
  
-   Concentrarsi sul comportamento esterno del sistema, indipendentemente dalla progettazione interna.  
  
-   Descrivere le esigenze di utenti e parti interessate con molta meno ambiguità rispetto al linguaggio naturale.  
  
-   Definire un glossario di termini coerente che possa essere usato da utenti, sviluppatori e tester.  
  
-   Ridurre gap e incoerenze nei requisiti.  
  
-   Ridurre il lavoro necessario per rispondere alle modifiche dei requisiti.  
  
-   Pianificare l'ordine in cui verranno sviluppate le funzionalità.  
  
-   Usare i modelli come base per i test di sistema, evidenziando una chiara relazione tra test e requisiti. Quando i requisiti cambiano, questa relazione consente di aggiornare i test correttamente, garantendo in tal modo che il sistema soddisfi i nuovi requisiti.  
  
 Un modello di requisiti offre un vantaggio maggiore se viene usato per concentrare le discussioni con gli utenti o i relativi rappresentanti e se viene riesaminato all'inizio di ogni iterazione. Non è necessario completarlo in dettaglio prima di scrivere il codice. Un'applicazione parzialmente funzionante, anche se molto semplificata, crea in genere una base di discussione dei requisiti con gli utenti molto più stimolante. Il modello consente di riepilogare in modo efficace i risultati di tali discussioni. Per ulteriori informazioni, vedere [utilizza i modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md).  
  
> [!NOTE]
>  In questi argomenti con "sistema" si intende il sistema o l'applicazione che si sta sviluppando. Potrebbe essere un'ampia raccolta di molti componenti software e hardware, una singola applicazione o un componente software all'interno di un sistema più grande. In ogni caso il modello di requisiti descrive il comportamento visibile dall'esterno del sistema, che sia tramite un'interfaccia utente o tramite un'API.  
  
## <a name="common-tasks"></a>Attività comuni  
 È possibile creare molte visualizzazioni diverse dei requisiti degli utenti.  Ogni visualizzazione fornisce un determinato tipo di informazioni.  Quando si creano queste visualizzazioni, è consigliabile spostarsi frequentemente dall'una all'altra. È possibile iniziare da qualsiasi visualizzazione.  
  
|Diagramma o documento|Informazioni descritte in un modello di requisiti|Sezione|  
|-------------------------|-----------------------------------------------|-------------|  
|Diagramma classi concettuali|Glossario dei tipi usati per descrivere i requisiti, ovvero dei tipi visibili nell'interfaccia del sistema.||  
|Documenti o elementi di lavoro aggiuntivi|Criteri di prestazioni, sicurezza, usabilità e affidabilità.|[Che descrivono requisiti di qualità del servizio](#QoSRequirements)|  
|Documenti o elementi di lavoro aggiuntivi|Regole e vincoli non specifici di un particolare caso di utilizzo|[Visualizzazione delle regole di business](#BusinessRules)|  
  
 La maggior parte dei tipi di diagrammi può essere usata per altri scopi. Per una panoramica dei tipi di diagrammi, vedere [creare modelli per app](../modeling/create-models-for-your-app.md).
  
##  <a name="a-namebusinessrulesa-showing-business-rules"></a><a name="BusinessRules"></a>Visualizzazione delle regole di Business  
 Una regola di business è un requisito non associato a un particolare caso di utilizzo e deve essere osservata in tutto il sistema.  
  
 Molte regole di business sono vincoli sulle relazioni tra le classi concettuali. È possibile scrivere queste *statico**regole business* come commenti associati alle relative classi di un diagramma classi concettuali. Ad esempio:  
  
 ![Regola nel commento associato alla classe Order. ] (../modeling/media/uml_reqmcd2.png "UML_ReqmCD2")  
  
 Le*regole di business dinamiche* vincolano le sequenze di eventi consentite. È possibile ad esempio usare un diagramma di attività o di sequenza per mostrare che un utente deve accedere prima di eseguire altre operazioni nel sistema.  
  
 Tuttavia, molte regole dinamiche possono essere illustrate più efficacemente e genericamente sostituendole con regole statiche. Ad esempio è possibile aggiungere un attributo booleano "Connesso" in una classe del modello di classi concettuali. L'attributo Connesso viene aggiunto come postcondizione della registrazione nel caso di utilizzo e come precondizione della maggior parte degli altri casi di utilizzo. Questo approccio consente di evitare di definire tutte le combinazioni possibili di sequenze di eventi. È anche più flessibile quando è necessario aggiungere nuovi casi di utilizzo al modello.  
  
 Si noti che la scelta in questo caso riguarda la modalità di definizione dei requisiti ed è indipendente dal modo in cui vengono implementati i requisiti nel codice programma.  
  
 Per altre informazioni, vedere gli argomenti seguenti:  
  
|Informazioni|Lettura|  
|--------------------|----------|  
|Come sviluppare codice che soddisfi le regole di business|[Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="a-nameqosrequirementsa-describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a>Che descrivono requisiti di qualità del servizio  
 Esistono diverse categorie di requisiti per la qualità del servizio. Di seguito vengono forniti alcuni esempi:  
  
-   Prestazioni  
  
-   Sicurezza  
  
-   Usabilità  
  
-   Affidabilità  
  
-   Efficienza  
  
 È possibile includere alcuni di questi requisiti nelle descrizioni di casi di utilizzo specifici. Gli altri requisiti non sono specifici dei casi di utilizzo e vengono scritti più efficacemente in un documento separato. Quando possibile, è utile rispettare il vocabolario definito dal modello di requisiti. Nell'esempio seguente le parole principali usate nel requisito sono i titoli di attori, casi di utilizzo e classi delle illustrazioni precedenti:  
  
 Se un Ristorante elimina un Elemento menu mentre un Cliente ordina un pasto, tutti gli Elementi ordine che fanno riferimento all'Elemento menu verranno visualizzati in rosso.  
  
 Per altre informazioni, vedere gli argomenti seguenti:  
  
|Informazioni|Lettura|  
|--------------------|----------|  
|Altre informazioni sulla registrazione dei requisiti di qualità del servizio|[Linee guida per la definizione di requisiti qualità del servizio](http://msdn.microsoft.com/en-us/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|Come sviluppare codice che soddisfi i requisiti di qualità del servizio|[Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare i modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)   
 [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)   
