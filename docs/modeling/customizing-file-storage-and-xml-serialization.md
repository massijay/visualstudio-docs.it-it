---
title: "Personalizzazione dell&#39;archiviazione dei file e della serializzazione XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.xmlbehavior"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, serializzazione"
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 17
---
# Personalizzazione dell&#39;archiviazione dei file e della serializzazione XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando l'utente salva un'istanza o *modello*, di un linguaggio specifico di dominio (DSL) in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], un file XML viene creato o aggiornato. Il file potrà essere ricaricato per ricreare il modello nell'archivio.  
  
 È possibile personalizzare lo schema di serializzazione, modificando le impostazioni in **il comportamento di serializzazione Xml** in Esplora DSL. È presente un nodo in **il comportamento di serializzazione Xml** per ogni classe di dominio, proprietà e relazioni. Le relazioni sono posizionate nella loro classi di origine. Esistono anche nodi corrispondenti alla forma, connettore e diagramma classi.  
  
 È anche possibile scrivere codice programma di personalizzazione più avanzata.  
  
> [!NOTE]
>  Se si desidera salvare il modello in un formato specifico, ma non è necessario ricaricare il file da tale modulo, considerare l'utilizzo di modelli di testo per generare l'output del modello, anziché uno schema di serializzazione personalizzata. Per ulteriori informazioni, vedere [la generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="model-and-diagram-files"></a>File di modello e diagramma  
 Ogni modello viene in genere salvata in due file:  
  
-   Il file del modello ha un nome, ad esempio **Model1.mydsl**. Archivia gli elementi del modello e le relazioni e le relative proprietà. L'estensione del file, ad esempio **.mydsl** varia a seconda di **FileExtension** proprietà del **Editor** nodo nella definizione DSL.  
  
-   Il file del diagramma ha un nome, ad esempio **Model1.mydsl.diagram**. Archivia le forme, connettori e le relative posizioni, i colori, spessori e altri dettagli dell'aspetto del diagramma. Se l'utente elimina un **.diagram** file, le informazioni importanti nel modello non vengono perse. Solo il layout del diagramma verrà perso. Quando viene aperto il file del modello, impostare un valore predefinito di forme e connettori verranno creati.  
  
#### <a name="to-change-the-file-extension-of-a-dsl"></a>Per modificare l'estensione del file di un linguaggio DSL  
  
1.  Aprire la definizione DSL. In Esplora DSL, fare clic sul nodo Editor.  
  
2.  Nella finestra Proprietà modificare il **FileExtension** proprietà. Non includere iniziale "." l'estensione di file.  
  
3.  In Esplora soluzioni, modificare il nome dei file di modello di due elementi in **DslPackage\ProjectItemTemplates**. Questi file hanno nomi che seguono questo formato:  
  
     `myDsl.diagram`  
  
     `myDsl.myDsl`  
  
## <a name="the-default-serialization-scheme"></a>Lo schema di serializzazione predefinito  
 Per creare un esempio di questo argomento, è stata utilizzata la seguente definizione DSL.  
  
 ![Diagramma di definizione DSL &#45; modello di albero genealogico](~/modeling/media/familyt_person.png "FamilyT_Person")  
  
 Questo DSL utilizzato per creare un modello che ha l'aspetto seguente sullo schermo.  
  
 ![Diagramma, casella degli strumenti e finestra di esplorazione dell'albero genealogico](~/modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 Questo modello è stato salvato e quindi riaperto nell'editor di testo XML:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">  
  <people>  
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">  
      <children>  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />  
      </children>  
    </person>  
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />  
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />  
  </people>  
</familyTreeModel>  
  
```  
  
 Notare gli aspetti seguenti relativi al modello serializzato:  
  
-   Tutti i nodi XML ha un nome che corrisponde al nome della classe un dominio, ad eccezione del fatto che la lettera iniziale è in minuscola. Ad esempio, `familyTreeModel` e `person`.  
  
-   Proprietà di dominio, ad esempio nome e DataNascita vengono serializzate come attributi in nodi XML. Anche in questo caso, il carattere iniziale del nome della proprietà viene convertito in caratteri minuscoli.  
  
-   Ogni relazione viene serializzato come un nodo XML nidificato finale di origine della relazione. Il nodo ha lo stesso nome della proprietà di ruolo di origine, ma con un carattere iniziale minuscola.  
  
     Ad esempio, nella definizione DSL, un ruolo denominato **persone** ha come origine di **FamilyTree** (classe).  Nel codice XML, questo è rappresentato dal nodo denominato `people` annidato all'interno di `familyTreeModel` nodo.  
  
-   L'entità finale di destinazione di ogni relazione di incorporamento viene serializzato come un nodo annidato sotto la relazione. Ad esempio, il `people` nodo contiene numerosi `person` nodi.  
  
-   L'entità finale di destinazione di ogni relazione di riferimento viene serializzato come un *moniker*, che consente di codificare un riferimento all'elemento di destinazione.  
  
     Ad esempio, in un `person` nodo può esistere un `children` relazione. Questo nodo contiene moniker, ad esempio:  
  
    ```  
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />  
    ```  
  
## <a name="understanding-monikers"></a>Informazioni sui moniker  
 Moniker vengono utilizzati per rappresentare i riferimenti incrociati tra diverse parti dei file di modello e diagramma. Vengono inoltre utilizzati nel `.diagram` file per fare riferimento ai nodi nel file del modello. Esistono due form del moniker:  
  
-   *Moniker ID* offerta il GUID dell'elemento di destinazione. Ad esempio:  
  
    ```  
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />  
  
    ```  
  
-   *Qualificato chiave moniker* identificare l'elemento di destinazione, il valore di una proprietà di dominio designato denominata chiave moniker. Il moniker dell'elemento di destinazione viene aggiunto come prefisso il moniker dell'elemento padre nell'albero delle relazioni di incorporamento.  
  
     Negli esempi seguenti vengono eseguiti da un linguaggio specifico di Dominio in cui vi è una classe di dominio denominata Album, che ha una relazione di incorporamento di un dominio denominata brano di classe:  
  
    ```  
    <albumMoniker title="/My Favorites/Jazz after Teatime" />  
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
  
    ```  
  
     Moniker chiave completo da utilizzare se la classe di destinazione dispone di una proprietà di dominio per cui l'opzione **chiave Moniker** è impostato su `true` in **il comportamento di serializzazione Xml**. Nell'esempio, questa opzione è impostata per le proprietà di dominio denominate "Title" nelle classi di dominio "Album" e "Brano".  
  
 Moniker chiave completo sono più facili da leggere rispetto a moniker ID. Se si intende il codice XML dei file di modello per la lettura da parte degli utenti, prendere in considerazione l'utilizzo di moniker chiave completo. Tuttavia, è possibile che all'utente di impostare più di un elemento per la stessa chiave moniker. Le chiavi duplicate potrebbero causare il file non di ricaricare correttamente. Pertanto, se si definisce una classe di dominio a cui fa riferimento l'utilizzo di moniker chiave completo, è consigliabile modi impedire all'utente di salvare un file con moniker duplicati.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Per impostare una classe di dominio moniker ID riferimento  
  
1.  Assicurarsi che **chiave Moniker** è `false` per ogni proprietà di dominio nella classe e le relative classi base.  
  
    1.  In Esplora DSL espandere **dati Behavior\Class di serializzazione Xml\\***\< classe di dominio>***\Element dati**.  
  
    2.  Verificare che **chiave Moniker** è `false` per ogni proprietà di dominio.  
  
    3.  Se la classe di dominio dispone di una classe base, ripetere la procedura in tale classe.  
  
2.  Impostare **serializza Id** = `true` per la classe di dominio.  
  
     Questa proprietà può trovarsi in **il comportamento di serializzazione Xml**.  
  
#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Per impostare una classe di dominio completo chiave moniker riferimento  
  
-   Impostare **chiave Moniker** per una proprietà di dominio di una classe di dominio esistente. Il tipo della proprietà deve essere `string`.  
  
    1.  In Esplora DSL espandere **dati Behavior\Class di serializzazione Xml\\***\< classe di dominio>***\Element dati**, quindi selezionare la proprietà di dominio.  
  
    2.  Nella finestra Proprietà impostare **chiave Moniker** per `true`.  
  
-   \- o -  
  
     Creare una nuova classe di dominio utilizzando il **classe di dominio denominata** strumento.  
  
     Questo strumento crea una nuova classe che dispone di una proprietà di dominio denominata Name. Il **è nome elemento** e **chiave Moniker** di questa proprietà di dominio vengono inizializzate per `true`.  
  
-   \- o -  
  
     Creare una relazione di ereditarietà dalla classe di dominio a un'altra classe che dispone di una proprietà chiave moniker.  
  
### <a name="avoiding-duplicate-monikers"></a>Evitare duplicati moniker  
 Se si utilizza moniker chiave completo, è possibile che due elementi nel modello a un utente potrebbero avere lo stesso valore in proprietà chiave. Ad esempio, se il linguaggio DSL è una classe Person che dispone di una proprietà nome, l'utente può impostare i nomi di due elementi dello stesso. Sebbene il modello può essere salvata in file, sarebbe non venga aggiornata correttamente.  
  
 Esistono diversi metodi che consentono di evitare questa situazione:  
  
-   Impostare **è nome elemento** = `true` per la proprietà chiave di dominio. Selezionare la proprietà di dominio nel diagramma di definizione DSL e quindi impostare il valore nella finestra Proprietà.  
  
     Quando l'utente crea una nuova istanza della classe, questo valore, la proprietà di dominio venga assegnato automaticamente un valore diverso. Il comportamento predefinito viene aggiunto un numero alla fine del nome della classe. Questo non impedisce all'utente di modifica del nome di un duplicato, ma risulta utile nel caso durante l'utente non viene impostato il valore prima di salvare il modello.  
  
-   Abilitare la convalida per il linguaggio DSL. In Esplora DSL, selezionare editor\convalida e impostare il **utilizza...** proprietà `true`.  
  
     Esiste un metodo di convalida generati automaticamente che controlla per ambiguità. Il metodo è incluso il `Load` categoria di convalida. In questo modo si garantirà che l'utente verrà avvertito che potrebbe non essere possibile riaprire il file.  
  
     Per ulteriori informazioni, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
### <a name="moniker-paths-and-qualifiers"></a>I qualificatori e i percorsi di moniker  
 Un moniker completo chiave termina con la chiave moniker ed è preceduto con il moniker dell'elemento padre nell'albero di incorporamento. Ad esempio, se il moniker di un Album è:  
  
```  
<albumMoniker title="/My Favorites/Jazz after Teatime" />  
  
```  
  
 Uno dei brani in tale Album quindi potrebbe essere:  
  
```  
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />  
```  
  
 Tuttavia, se album fa riferimento a ID invece, il moniker sarà come segue:  
  
```  
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />  
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />  
```  
  
 Si noti che poiché un GUID è univoco, mai preceduto dal moniker del relativo padre.  
  
 Se si sa che una proprietà di dominio particolare abbia sempre un valore univoco all'interno di un modello, è possibile impostare **qualificatore di Moniker è** a `true` per quella proprietà. In questo modo potrà essere utilizzato come qualificatore, senza utilizzare il moniker dell'elemento padre. Ad esempio, se si impostano entrambe **qualificatore di Moniker è** e **chiave Moniker** per la proprietà di dominio del titolo della classe Album, nome o l'identificatore del modello non viene utilizzato nel moniker per Album e i relativi figli incorporato:  
  
```  
<albumMoniker name="Jazz after Teatime" />  
<songMoniker title="/Jazz after Teatime/Hot tea" />  
  
```  
  
## <a name="customizing-the-structure-of-the-xml"></a>La struttura del XML di personalizzazione  
 Per apportare le seguenti personalizzazioni, espandere il **il comportamento di serializzazione Xml** nodo in Esplora DSL. In una classe di dominio, espandere il nodo dell'elemento dati per visualizzare l'elenco di proprietà e relazioni che hanno origine in questa classe. Selezionare una relazione e modificare le opzioni nella finestra Proprietà.  
  
-   Impostare **elemento omettere** su true per omettere il nodo di ruolo di origine, lasciando solo l'elenco di elementi di destinazione. Non impostare questa opzione se non esiste più di una relazione tra le classi di origine e di destinazione.  
  
    ```  
  
    <familyTreeModel ...>  
      <!-- The following node is omitted by using Omit Element: -->  
      <!-- <people> -->  
        <person name="Henry VIII" .../>  
        <person name="Elizabeth I" .../>  
      <!-- </people> -->  
    </familyTreeModel>  
  
    ```  
  
-   Impostare **forma completa utilizzare** per incorporare i nodi di destinazione in nodi che rappresentano le istanze di relazione. Questa opzione viene impostata automaticamente quando si aggiungono le proprietà del dominio a una relazione di dominio.  
  
    ```  
  
    <familyTreeModel ...>  
      <people>  
        <!-- The following node is inserted by using Use Full Form: -->  
        <familyTreeModelHasPeople myRelationshipProperty="x1">  
          <person name="Henry VIII" .../>  
        </familyTreeModelHasPeople>  
        <familyTreeModelHasPeople myRelationshipProperty="x2">  
          <person name="Elizabeth I" .../>  
        </familyTreeModelHasPeople>  
      </people>  
    </familyTreeModel>  
  
    ```  
  
-   Impostare **rappresentazione** = **elemento** di una proprietà di dominio salvata come un elemento anziché come valore dell'attributo.  
  
    ```  
    <person name="Elizabeth I" birthYear="1533">  
      <deathYear>1603</deathYear>  
    </person>  
    ```  
  
-   Per modificare l'ordine in cui vengono serializzate gli attributi e relazioni, fare doppio clic su un elemento sotto l'elemento dati e utilizzare il **Sposta su** o **Sposta giù** i comandi di menu.  
  
## <a name="major-customization-using-program-code"></a>Personalizzazione principale tramite il codice programma  
 È possibile sostituire parti o tutti gli algoritmi di serializzazione.  
  
 Si consiglia di esaminare il codice in **Dsl\Generated Code\Serializer.cs** e **SerializationHelper.cs**.  
  
#### <a name="to-customize-the-serialization-of-a-particular-class"></a>Per personalizzare la serializzazione di una determinata classe  
  
1.  Impostare **personalizzato** nel nodo per tale classe in **il comportamento di serializzazione Xml**.  
  
2.  Trasforma tutti i modelli, compilare la soluzione e analizzare gli errori di compilazione risultante. Commenti quasi ogni errore viene illustrato il codice è necessario fornire.  
  
#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Per fornire la serializzazione personalizzata per l'intero modello  
  
1.  Override dei metodi in Dsl\GeneratedCode\SerializationHelper.cs  
  
## <a name="options-in-xml-serialization-behavior"></a>Opzioni di comportamento di serializzazione Xml  
 In Esplora DSL, il nodo di comportamento di serializzazione Xml contiene un nodo figlio per ogni classe di dominio, relazione, forma, connettore e classe diagramma. In ciascuno di questi nodi è un elenco di proprietà e relazioni originate in quell'elemento. Le relazioni sono rappresentate in proprio a destra e sotto le classi di origine.  
  
 Nella tabella seguente vengono riepilogate le opzioni che è possibile impostare in questa sezione della definizione DSL. In ogni caso, selezionare un elemento in Esplora DSL e impostare le opzioni nella finestra Proprietà.  
  
### <a name="xml-class-data"></a>Dati XML (classe)  
 Questi elementi si trovano in Esplora DSL sotto **dati Behavior\Class di serializzazione Xml**.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|È l'elemento personalizzato dello Schema|Se True, indica che la classe di dominio ha uno schema di elemento personalizzato|  
|Personalizzato|Impostare questa proprietà su **True** Se si desidera scrivere codice di serializzazione e deserializzazione per questa classe di dominio.<br /><br /> Compilare la soluzione ed esaminare gli errori per individuare le istruzioni dettagliate.|  
|Classe di dominio|Classe di dominio a cui si applica questo nodo di dati di classe. Sola lettura.|  
|Nome elemento|Nome del nodo XML per gli elementi di questa classe. Il valore predefinito è una versione minuscola del nome della classe di dominio.|  
|Nome dell'attributo moniker|Nome dell'attributo utilizzato per contenere il riferimento negli elementi moniker. Se è vuota, viene utilizzato il nome della proprietà chiave o id.<br /><br /> In questo esempio è "name":  `<personMoniker name="/Mike Nash"/>`|  
|Nome dell'elemento moniker|Nome dell'elemento xml utilizzato per moniker che fanno riferimento agli elementi di questa classe.<br /><br /> Il valore predefinito è una versione in lettere minuscole del nome della classe presenta il suffisso "Moniker". Ad esempio `personMoniker`.|  
|Nome del tipo di moniker|Nome del tipo xsd generato per moniker agli elementi di questa classe. Lo schema XSD è **codice Dsl\Generated\\\*schema. xsd**|  
|Serializzare Id|Se True, l'elemento GUID è incluso nel file. Deve essere true se è presente alcuna proprietà che è contrassegnata **chiave Moniker** e il linguaggio DSL definisce le relazioni di riferimento di questa classe.|  
|Nome tipo|Nome del tipo xml generato in xsd dalla classe di dominio designato.|  
|Note|Note informali associate all'elemento|  
  
### <a name="xml-property-data"></a>Dati di proprietà XML  
 Nodi di proprietà XML si trovano sotto i nodi della classe.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|Proprietà di dominio|Proprietà a cui si applicano i dati di configurazione della serializzazione xml. Sola lettura.|  
|Chiave Moniker|Se True, la proprietà viene utilizzata come chiave per la creazione di moniker che fanno riferimento a istanze di questa classe di dominio.|  
|Qualificatore di Moniker|Se True, la proprietà viene utilizzata per la creazione il qualificatore di moniker. Se false, e se SerializeId non è valido per questa classe di dominio, moniker sono qualificati dal moniker dell'elemento padre nell'albero di incorporamento.|  
|Rappresentazione|Se l'attributo, la proprietà viene serializzato come attributo xml; Se l'elemento è serializzato come elemento. Se Ignora, non è serializzato.|  
|Nome XML|Nome utilizzato per l'elemento che rappresenta la proprietà o un attributo xml. Per impostazione predefinita, questa è una versione minuscola del nome della proprietà di dominio.|  
|Note|Note informali associate all'elemento|  
  
### <a name="xml-role-data"></a>Dati del ruolo di XML  
 Nodi dati ruolo si trovano sotto i nodi di classe di origine.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|Dispone di Moniker personalizzato|Impostare su true se si desidera fornire il proprio codice per la generazione e la risoluzione di moniker che passano attraverso questa relazione.<br /><br /> Per istruzioni dettagliate, compilare la soluzione e quindi fare doppio clic su messaggi di errore.|  
|Relazione di dominio|Specifica la relazione in cui queste opzioni si applicano. Sola lettura.|  
|Omettere l'elemento|Se true, il nodo XML che corrisponde al ruolo di origine viene omesso dallo schema.<br /><br /> Se è presente più di una relazione tra le classi di origine e di destinazione, questo nodo ruolo distingue tra i collegamenti che appartengono a due relazioni. È pertanto consigliabile non impostare questa opzione in questo caso.|  
|Nome dell'elemento ruolo|Specifica il nome dell'elemento XML che dipende dal ruolo di origine. Il valore predefinito è il nome di proprietà del ruolo.|  
|Utilizzare il modulo completo|Se true, ogni elemento di destinazione o di un moniker è racchiusa tra un nodo XML che rappresenta la relazione. Questo deve essere impostato su true se la relazione presenta proprietà dominio.|  
  
## <a name="see-also"></a>Vedere anche  
 [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)