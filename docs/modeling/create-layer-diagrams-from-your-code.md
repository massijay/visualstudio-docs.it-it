---
title: Creare diagrammi di dipendenza dal codice | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: b17d12160920952170d042eb46191df66542c80a
ms.openlocfilehash: e51f32303496d20980d7442458cd35350db01687
ms.lasthandoff: 02/22/2017

---
# <a name="create-dependency-diagrams-from-your-code"></a>Creare diagrammi di dipendenza dal codice
Per visualizzare l'architettura di alto livello, logica del sistema software, creare un *diagramma dipendenze* in Visual Studio. Per assicurarsi che il codice rimanga coerenza con la progettazione, convalidare il codice con un diagramma di dipendenze. È possibile creare diagrammi di dipendenza per i progetti Visual c# .NET e Visual Basic .NET. Per informazioni sulle versioni di Visual Studio che supportano questa funzionalità, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Creare un diagramma di dipendenze](~/modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Un diagramma di dipendenza consente di organizzare gli elementi di soluzione Visual Studio in gruppi logici e astratti denominati *livelli*. È possibile utilizzare i livelli per descrivere le attività principali che tali elementi eseguono oppure i componenti principali del sistema. Ogni livello può contenere altri livelli che descrivono attività più dettagliate. È inoltre possibile specificare il desiderate o esistenti *dipendenze* tra livelli. Tali dipendenze, rappresentate come frecce, mostrano quali livelli possono utilizzare o utilizzano attualmente la funzionalità rappresentata da altri livelli. Per gestire controllo a livello di architettura nel codice, mostrare le dipendenze desiderate nel diagramma, quindi convalidare il codice in base al diagramma.  
  
 [Video: Convalidare le dipendenze di architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 
  
##  <a name="a-namecreatediagrama-create-a-dependency-diagram"></a><a name="CreateDiagram"></a>Creare un diagramma di dipendenza  
 Prima di creare un diagramma di dipendenze, assicurarsi che la soluzione contiene un progetto di modellazione. 
  
> [!IMPORTANT]
>  Non aggiungere, trascinare o copiare un diagramma di dipendenza esistente da un progetto di modellazione in un altro progetto di modellazione o in un'altra posizione nella soluzione. In questo modo i riferimenti del diagramma originale verranno mantenuti, anche se si modifica il diagramma. In caso contrario, il funzionamento della convalida dei livelli non sarà corretto e potrebbero verificarsi altri problemi, quali la mancanza di elementi o altri errori quando si tenta di aprire il diagramma.  
>   
>  Al contrario, aggiungere un nuovo diagramma di dipendenza per il progetto di modello. copiare gli elementi dal diagramma di origine al nuovo diagramma Salvare il progetto di modellazione e il nuovo diagramma di dipendenza.  
  
#### <a name="to-add-a-new-dependency-diagram-to-a-modeling-project"></a>Per aggiungere un nuovo diagramma di dipendenza a un progetto di modellazione  
  
1.  Nel **architettura** menu, scegliere **nuovo diagramma dipendenza**.  
  
2.  In **modelli**, scegliere **diagramma dipendenze**.  
  
3.  Assegnare un nome al diagramma.  
  
4.  In **Aggiungi a progetto di modello**, individuare e selezionare un progetto di modellazione esistente nella soluzione.  
  
     -oppure-  
  
     Scegliere **creare un nuovo progetto di modellazione** per aggiungere un nuovo progetto di modellazione alla soluzione.  
  
    > [!NOTE]
    >  Il diagramma di dipendenza deve esistere all'interno di un progetto di modellazione. È tuttavia possibile collegarlo a elementi in qualsiasi punto della soluzione.  
  
5.  Assicurarsi di salvare il progetto di modellazione e il diagramma di dipendenze.  

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Trascinare e rilasciare, oppure copiare e incollare, da una mappa di codice

1. Generare una mappa di codice per la soluzione usando il **architettura** menu. 

2. È possibile applicare un filtro mappa di codice per rimuovere le cartelle della soluzione e "Risorse di Test" Se si desidera applicare le dipendenze nel codice di prodotto.

3. Sulla mappa codice generato, rimuovere il nodo "Esterno", o espansa per visualizzare gli assembly esterni, a seconda se si desidera applicare le dipendenze dello spazio dei nomi ed eliminare gli assembly non necessari dalla mappa codici. 

4. Creare un nuovo diagramma di dipendenza per la soluzione usando il **architettura** menu

5. Selezionare tutti i nodi nella mappa di codice (utilizzare _Ctrl_ + _A_, oppure utilizzare la selezione elastica premendo il _MAIUSC_ chiave prima di fare clic su, trascinare e rilasciare.

6. Trascinamento e rilascio, o una copia e Incolla, gli elementi selezionati per il nuovo diagramma di convalida della dipendenza. 

7. Mostra l'architettura dell'applicazione corrente. Decidere l'architettura sia desiderato e modificare di conseguenza il diagramma di dipendenze.

![Diagramma di dipendenze generato da una mappa codici](~/modeling/media/dependency-validation-01.png)
  
##  <a name="a-namecreatelayersa-create-layers-from-artifacts"></a><a name="CreateLayers"></a>Creare livelli da elementi  
 È possibile creare livelli da elementi presenti in una soluzione di Visual Studio, ad esempio progetti, file di codice, spazi dei nomi, classi e metodi. In questo modo vengono creati automaticamente collegamenti tra livelli ed elementi, che vengono inclusi nel processo di convalida dei livelli.  
  
 È inoltre possibile collegare livelli a elementi che non supportano la convalida, ad esempio documenti Word o presentazioni PowerPoint, in modo da associare un livello con specifiche o piani. È anche possibile collegare livelli a file di progetti condivisi tra più applicazioni, ma il processo di convalida non includerà tali livelli, che vengano visualizzati con nomi generici come "Livello 1" e "Livello 2".  
  
 Per vedere se un elemento collegato supporta la convalida, aprire **Esplora livello** ed esaminare il **convalida supporti** proprietà dell'elemento. Vedere [la gestione dei collegamenti agli elementi](#Managing).  
  
|**Per**|**Seguire questi passaggi**|  
|------------|----------------------------|  
|Creare un livello per un solo artefatto|<ol><li>Trascinare l'elemento nel diagramma delle dipendenze da queste origini:<br /><br /> <ul><li>**Esplora soluzioni**<br /><br />         Ad esempio, è possibile trascinare file o progetti.</li><li>Mappe codice<br /><br />         Vedere [mappare le dipendenze delle soluzioni](../modeling/map-dependencies-across-your-solutions.md) e [usare le mappe codice per il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Visualizzazione classi** o **Visualizzatore oggetti**</li></ul><br />     Nel diagramma viene visualizzato un livello collegato all'artefatto.</li><li>Rinominare il livello per riflettere le responsabilità del codice o degli artefatti associati.</li></ol> **Importante:** trascinando i file binari per il diagramma di dipendenze non vengono aggiunti automaticamente i riferimenti al progetto di modellazione. ma è necessario aggiungere manualmente i file binari desiderati per convalidare il progetto di modellazione. **Per aggiungere file binari al progetto di modellazione** <ol><li>In **Esplora**, aprire il menu di scelta rapida per il progetto di modello e quindi scegliere **Aggiungi elemento esistente**.</li><li>Nel **Aggiungi elemento esistente** la finestra di dialogo, individuare i file binari, selezionarli, quindi scegliere **OK**.     I file binari verranno visualizzati nel progetto di modellazione.</li><li>In **Esplora**, scegliere un file binario aggiunto e quindi premere **F4** per aprire la **proprietà** finestra.</li><li>Per ogni file binario, impostare il **operazione di compilazione** proprietà **convalida**.</li></ol>|  
|Creare un solo livello per tutti gli artefatti selezionati|Trascinare contemporaneamente tutti gli elementi nel diagramma di dipendenza.<br /><br /> Nel diagramma viene visualizzato un livello collegato a tutti gli artefatti.|  
|Creare un livello per ogni artefatto selezionato|Premere e tenere premuto il **MAIUSC** mentre si trascinano contemporaneamente tutti gli elementi nel diagramma delle dipendenze. **Nota:** se si utilizza il **MAIUSC** per selezionare un intervallo di elementi, rilasciare il tasto dopo avere selezionato gli elementi. Premerlo e tenerlo premuto nuovamente quando si trascinano gli artefatti nel diagramma. <br /><br /> Per ogni elemento nel diagramma viene visualizzato un livello collegato a ciascun elemento.|  
|Aggiungere un elemento a un livello|Trascinare l'elemento sul livello.|  
|Creare un nuovo livello non collegato|Nel **della casella degli strumenti**, espandere il **diagramma dipendenze** sezione e quindi trascinare un **livello** al diagramma di dipendenza.<br /><br /> Per aggiungere più livelli, fare doppio clic sullo strumento. Al termine, scegliere il **puntatore** strumento o premere il **ESC** chiave.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per il diagramma delle dipendenze, scegliere **Aggiungi**, quindi scegliere **livello**.|  
|Creare livelli annidati|Trascinare un livello esistente su un altro livello.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per un livello, scegliere **Aggiungi**, quindi scegliere **livello**.|  
|Creare un nuovo livello contenente due o più livelli esistenti|Selezionare i livelli, aprire il menu di scelta rapida per la selezione e quindi scegliere **gruppo**.|  
|Modificare il colore di un livello|Impostare il relativo **colore** proprietà sul colore desiderato.|  
|Specificare che gli artefatti associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello di **Forbidden Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello di **Forbidden Namespace Dependencies** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello di **Required Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
  
 Il numero raffigurato sul livello indica il numero di artefatti a esso collegati. Tuttavia, nell'interpretazione di tale numero, considerare quanto segue:  
  
-   Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.  
  
     Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.  
  
-   Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.  
  
##  <a name="a-namemanaginga-manage-links-between-layers-and-artifacts"></a><a name="Managing"></a>Gestire collegamenti tra livelli ed elementi  
  
1.  Nel diagramma delle dipendenze, aprire il menu di scelta rapida per il livello e quindi scegliere **Visualizza collegamenti**.  
  
     **Esplora livello** Mostra i collegamenti dell'elemento per il livello selezionato.  
  
2.  Utilizzare le seguenti attività per gestire tali collegamenti:  
  
|**Per**|**In Esplora livello**|  
|------------|---------------------------|  
|Eliminare il collegamento tra il livello e un artefatto|Aprire il menu di scelta rapida per il collegamento all'elemento e quindi scegliere **eliminare**.|  
|Spostare il collegamento da un livello a un altro|Trascinare il collegamento dell'elemento in un livello esistente del diagramma.<br /><br /> -oppure-<br /><br /> 1.  Aprire il menu di scelta rapida per il collegamento all'elemento e quindi scegliere **Taglia**.<br />2.  Nel diagramma delle dipendenze, aprire il menu di scelta rapida per il livello e quindi scegliere **Incolla**.|  
|Copiare il collegamento da un livello a un altro|1.  Aprire il menu di scelta rapida per il collegamento all'elemento e quindi scegliere **copia**.<br />2.  Nel diagramma delle dipendenze, aprire il menu di scelta rapida per il livello e quindi scegliere **Incolla**.|  
|Creare un nuovo livello da un collegamento dell'artefatto esistente|Trascinare il collegamento dell'artefatto in un'area vuota del diagramma.|  
|Verificare che un elemento collegato supporti la convalida rispetto al diagramma di dipendenza.|Esaminare il **supporta la convalida** colonna per il collegamento all'elemento.|  
  
##  <a name="a-namediscoveringa-reverse-engineer-existing-dependencies"></a><a name="Discovering"></a>Decompilare dipendenze esistenti  
 È presente una dipendenza quando un artefatto associato a un livello dispone di un riferimento a un artefatto associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. È possibile decompilare dipendenze esistenti per elementi collegati a livelli nel diagramma.  
  
> [!NOTE]
>  Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per verificare quali elementi sono associate dipendenze che è possibile decompilare, aprire il menu di scelta rapida per uno o più livelli e quindi scegliere **Visualizza collegamenti**. In **Esplora livello**, esaminare il **supporta la convalida** colonna. Le dipendenze non verranno decompilate per elementi per cui questa colonna viene visualizzato **False**.  
  
-   Selezionare uno o più livelli, aprire il menu di scelta rapida per un livello selezionato e quindi scegliere **genera dipendenze**.  
  
 In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.  
  
##  <a name="a-nameeditdependenciesa-edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a>Modificare livelli e dipendenze per visualizzare la progettazione desiderata  
 Per descrivere le modifiche da apportare al sistema o l'architettura desiderata, modificare il diagramma delle dipendenze:  
  
|**Per**|**Eseguire questi passaggi**|  
|------------|-----------------------------|  
|Modificare o limitare la direzione di una dipendenza|Impostare il relativo **direzione** proprietà.|  
|Creare nuove dipendenze|Utilizzare il **dipendenza** e **dipendenza bidirezionale** strumenti.<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, scegliere il **puntatore** strumento o premere il **ESC** chiave.|  
|Specificare che gli artefatti associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello di **Forbidden Namespace Dependencies** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello di **Forbidden Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello di **Required Namespaces** proprietà. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
  
##  <a name="a-nameeditlayouta-change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a>Modificare la modalità di visualizzazione degli elementi nel diagramma  
 È possibile modificare la dimensione, la forma, il colore e la posizione dei livelli o il colore delle dipendenze modificandone le proprietà.  
  
##  <a name="a-namecodemapsa-discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a>Individuare i motivi e le dipendenze in una mappa codici  
 Durante la creazione di diagrammi di dipendenza, è possibile creare anche **mappe codici**. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti per esplorare assembly, spazi dei nomi e classi, che spesso corrispondono ai livelli esistenti. Per altre informazioni sulle mappe codice, vedere:  
  
-   [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Video: Convalidare le dipendenze di architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
 [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)   
 [Diagrammi di dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md)   
 [Convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)   
 [Visualizzare il codice](../modeling/visualize-code.md)

