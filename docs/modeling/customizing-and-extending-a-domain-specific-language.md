---
title: Personalizzazione ed estensione di un linguaggio specifico di dominio | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 48
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 00a120fc470393f8ab843636ca5d3400b004232b
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personalizzazione ed estensione di un linguaggio specifico di dominio
Visual Studio Modeling e visualizzazione SDK (VMSDK) sono disponibili vari livelli in cui è possibile definire gli strumenti di modellazione:  
  
1.  Definire un linguaggio specifico di dominio (DSL) utilizzando il diagramma di definizione DSL. È possibile creare rapidamente un linguaggio DSL con una notazione basata su diagramma, un formato XML leggibile e gli strumenti di base necessari per generare il codice e altri elementi.  
  
     Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Ottimizzare il linguaggio DSL utilizzando le funzionalità più avanzate della definizione DSL. Ad esempio, è possibile creare collegamenti aggiuntivi vengono visualizzati quando l'utente crea un elemento. Queste tecniche vengono realizzate per lo più nella definizione DSL e alcune richiedono poche righe di codice programma.  
  
3.  Estendere gli strumenti di modellazione usando codice programma. VMSDK è progettato in modo specifico per facilitare l'integrazione delle estensioni con il codice generato dalla definizione DSL.  Per ulteriori informazioni, vedere [la scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Dopo aver aggiornato il file di definizione DSL, non dimenticare di fare clic su **Trasforma tutti i modelli** sulla barra degli strumenti di Esplora soluzioni prima di ricompilare la soluzione.  
  
##  <a name="a-namecustomshapesa-in-this-section"></a><a name="customShapes"></a>In questa sezione  
  
|Per ottenere questo effetto|Fare riferimento a questo argomento|  
|----------------------------|-------------------------|  
|Consentire all'utente di impostare le proprietà di colore e stile di una forma.|Fare clic su classe forma o connettore, scegliere **Aggiungi esposta**, fare clic su un elemento.<br /><br /> Vedere [personalizzazione della presentazione nel diagramma](../modeling/customizing-presentation-on-the-diagram.md).|  
|Diverse classi di elemento del modello simile nel diagramma, la condivisione di proprietà, ad esempio l'altezza iniziale e la larghezza, colore, le descrizioni comandi.|Utilizzare l'ereditarietà tra le forme o le classi di connettore. I mapping tra le forme derivate e classi di dominio derivate ereditano i dettagli di mapping di elementi padre.<br /><br /> In alternativa, eseguire il mapping di classi di dominio diverso per la stessa classe shape.|  
|Una classe di elemento del modello viene visualizzata da contesti di diverse forme.|Eseguire il mapping di più di una classe di forma nella stessa classe di dominio. Quando si compila la soluzione, seguire la segnalazione errori e fornire il codice richiesto per decidere quale forma da utilizzare.|  
|Colore della forma o altre funzionalità, ad esempio tipo di carattere indicano lo stato corrente.|Vedere [aggiornare forme e connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Creare una regola che aggiorna le proprietà esposte. Vedere [le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> In alternativa, utilizzare OnAssociatedPropertyChanged() per l'aggiornamento non esposti da funzionalità quali le frecce di collegamento o tipo di carattere.|  
|Icona su Cambia forma per indicare lo stato.|Impostare la visibilità del mapping dell'elemento decorator nella finestra Dettagli DSL. Individuare gli elementi Decorator immagine diversi nella stessa posizione. Vedere [aggiornare forme e connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> In alternativa, eseguire l'override `ImageField.GetDisplayImage()`. Vedere l'esempio in <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>|  
|Impostare un'immagine di sfondo per qualsiasi forma|Eseguire l'override per aggiungere un ancoraggio ImageField InitializeInstanceResources(). Vedere [personalizzazione della presentazione nel diagramma](../modeling/customizing-presentation-on-the-diagram.md).|  
|Annidare forme a qualsiasi profondità|Consente di impostare una ricorsiva incorporamento di struttura ad albero. Definire BoundsRules per contenere le forme. Vedere [personalizzazione della presentazione nel diagramma](../modeling/customizing-presentation-on-the-diagram.md).|  
|Collegare i connettori momenti fisso sul bordo dell'elemento.|Definire elementi terminali incorporati, rappresentati dalle porte di piccole dimensioni nel diagramma. Per risolvere le porte sul posto, utilizzare BoundsRules. Vedere l'esempio di diagramma circuito in [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Campo di testo viene visualizzato un valore derivato da altri valori.|Mapping elemento decorator testo a una proprietà di dominio calcolata o di archiviazione personalizzato. Per ulteriori informazioni, vedere [calcolati e le proprietà di archiviazione personalizzato](../modeling/calculated-and-custom-storage-properties.md).|  
|Propagare le modifiche tra gli elementi del modello o tra forme|Vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).|  
|Propagare le modifiche alle risorse, ad esempio altri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensioni all'esterno dell'archivio.|Vedere [i gestori eventi propagano le modifiche apportate all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Finestra delle proprietà consente di visualizzare le proprietà di un elemento correlato.|Impostare la proprietà di inoltro. Vedere [personalizzazione della finestra proprietà](../modeling/customizing-the-properties-window.md).|  
|Categorie di proprietà|La finestra proprietà è divisa in sezioni denominate le categorie. Impostare il **categoria** delle proprietà di dominio. Proprietà con lo stesso nome di categoria verranno visualizzate nella stessa sezione. È inoltre possibile impostare il **categoria** di un ruolo di relazione.|  
|Controllare l'accesso utente alle proprietà di dominio|Impostare **è esplorabile** false per evitare che una proprietà di dominio venga visualizzato nella finestra proprietà in fase di esecuzione. È comunque possibile mappare a elementi Decorator testo.<br /><br /> **È di sola lettura dell'interfaccia utente** impedisce la modifica di una proprietà di dominio.<br /><br /> Accesso ai programmi per la proprietà di dominio non è interessato.|  
|Modificare il nome, l'icona e visibilità di nodi in Esplora modelli del linguaggio DSL.|Vedere [personalizzazione di Esplora modelli](../modeling/customizing-the-model-explorer.md).|  
|Abilitare la copia, Taglia e Incolla|Impostare il **Abilita Copia/Incolla** proprietà di **Editor** nodo in Esplora DSL.|  
|Copiare i relativi obiettivi e i collegamenti di riferimento ogni volta che viene copiato un elemento. Ad esempio, copiare i commenti associati a un elemento.|Impostare il **propaga copia** proprietà del ruolo di origine (rappresentato dalla linea su un lato della relazione di dominio nel diagramma di definizione DSL).<br /><br /> Scrivere codice per eseguire l'override ProcessOnCopy per ottenere effetti più complessi.<br /><br /> Vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|  
|Eliminare, reimpostato o ricollegare gli elementi correlati quando viene eliminato un elemento.|Impostare il **Propaga eliminazione** valore di un ruolo di relazione. Per ottenere effetti più complessi, eseguire l'override `ShouldVisitRelationship` e `ShouldVisitRolePlayer` metodi di `MyDslDeleteClosure` , definita in **DomainModel.cs**<br /><br /> Vedere [personalizzazione del comportamento di eliminazione](../modeling/customizing-deletion-behavior.md)|  
|Mantenere il layout di forme e aspetto nella copia e trascinamento.|Aggiungere le forme e connettori copiato `ElementGroupPrototype`. Il metodo più semplice per eseguire l'override`ElementOperations.CreateElementGroupPrototype()`<br /><br /> Vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|  
|Incollare le forme in una posizione prescelta, ad esempio la posizione del cursore attuale.|Eseguire l'override `ClipboardCommandSet.ProcessOnCopy()` per utilizzare la versione del percorso specifica `ElementOperations.Merge().` vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|  
|Creare collegamenti aggiuntivi quando si incolla|Eseguire l'override ClipboardCommandSet.ProcessOnPasteCommand()|  
|Abilitare il trascinamento dal diagramma, altri linguaggi specifici di dominio e Windows elementi|Vedere [procedura: aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Consente di forma o strumenti è possibile trascinare una forma figlio, ad esempio una porta, come se si sono stato trascinato l'elemento padre.|Definire una direttiva di unione degli elementi nella classe di oggetto di destinazione, per inoltrare l'oggetto rilasciato per l'elemento padre. Vedere [personalizzazione lo spostamento e la creazione degli elementi](../modeling/customizing-element-creation-and-movement.md).|  
|Consentire una forma o lo strumento è possibile trascinare una forma e collegamenti aggiuntivi o gli oggetti creati. Ad esempio, per consentire a trascinare un elemento a cui è possibile collegare un commento.|Definire una direttiva di unione degli elementi nella classe di dominio di destinazione e definire i collegamenti da generare. In scenari complessi, è possibile aggiungere codice personalizzato. Vedere [personalizzazione lo spostamento e la creazione degli elementi](../modeling/customizing-element-creation-and-movement.md).|  
|Creare un gruppo di elementi con uno strumento. Ad esempio, un componente con un set fisso di porte.|Eseguire l'override del metodo di inizializzazione della casella degli strumenti in ToolboxHelper.cs. Creare un prototipo di gruppo elemento (EGP) che contiene gli elementi e i relativi collegamenti di relazione. Vedere [personalizzazione di strumenti e la casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Includere le forme dell'entità e la porte nel EGP oppure definire BoundsRules per posizionare le forme porta quando viene creata un'istanza di EGP. Vedere [(BoundsRules) vincolano posizione e dimensione](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Utilizzare uno strumento di connessione per creare diversi tipi di relazione.|Aggiungere direttive di collegamento connessione (LCD) per il generatore di connessione che viene richiamata dallo strumento. Il monitor LCD a determinare il tipo della relazione tra i tipi dei due elementi. Per rendere questo dipendono gli stati degli elementi, è possibile aggiungere codice personalizzato. Vedere [personalizzazione di strumenti e la casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md).|  
|Strumenti Sticky-l'utente può fare doppio clic su qualsiasi strumento per creare molte forme o connettori in successione.|In Esplora DSL, selezionare il `Editor` nodo. Nella finestra Proprietà impostare **utilizza permanenti gli elementi della casella degli strumenti**.|  
|Definire i comandi di menu|Vedere [procedura: modificare un comando di Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Vincolare il modello con le regole di convalida|Vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)|  
|Generare codice, i file di configurazione o documenti da un linguaggio DSL.|[Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Personalizzare la modalità con cui i modelli vengono salvati in file.|Vedere [personalizzazione di archiviazione di File e la serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Salvare i modelli di database o altri supporti.|Eseguire l'override *Linguaggioutente*documento DocData<br /><br /> Vedere [personalizzazione di archiviazione di File e la serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Integrare più linguaggi specifici di dominio in modo che funzionino come parte di un'applicazione.|Vedere [l'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Consentire il linguaggio DSL possono essere estesi da terze parti e l'estensione di controllo.|[Estendere il DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Condivisione di classi tra DSL usando una libreria DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definizione di un criterio di blocco per creare segmenti di sola lettura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


