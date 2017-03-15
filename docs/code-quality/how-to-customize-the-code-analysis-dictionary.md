---
title: "Procedura: Personalizzare il dizionario di analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dizionario di analisi del codice"
  - "dizionario personalizzato, analisi codice"
  - "dizionario, analisi codice"
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# Procedura: Personalizzare il dizionario di analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'analisi codice utilizza un dizionario integrato per controllare gli identificatori presenti nel codice e verificare l'assenza di errori ortografici, di maiuscole e minuscole e di altre convenzioni di denominazione in base alle linee guida di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  È possibile creare un file xml del dizionario personalizzato per aggiungere, rimuovere o modificare termini, abbreviazioni e acronimi nel dizionario incorporato.  
  
 Se ad esempio il codice contiene una classe denominata **contraccolpo**,  L'analisi codice identifica il nome come un insieme di due parole: **contrac** e **colpo**.  A questo punto, verrà generato un avviso in cui è indicato che il termine **contrac** non è ortograficamente corretto.  Per forzare l'analisi codice al riconoscimento dell'ortografia, è possibile aggiungere il termine **contrac** al dizionario personalizzato.  
  
## Per creare un dizionario personalizzato  
 Creare un file denominato **DizionarioPersonale.xml**.  
  
 Definire le parole personalizzate mediante la struttura XML seguente:  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>knokker</Word>  
         </Unrecognized>  
         <Recognized>  
            <Word></Word>  
         </Recognized>  
         <Deprecated>  
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
         </Compound>  
         <DiscreteExceptions>  
            <Term></Term>  
         </DiscreteExceptions>  
      </Words>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym></Acronym>  
         </CasingExceptions>  
      </Acronyms>  
   </Dictionary>  
```  
  
## Elementi del dizionario personalizzato  
 È possibile modificare il comportamento dell'analisi codice di dizionario aggiungendo termini come testo interno degli elementi seguenti nel dizionario personalizzato:  
  
-   [Dictionary/Words/Recognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [Dictionary/Words/Unrecognized/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [Dictionary/Words/Deprecated/Term[@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [Dictionary/Words/Compound/Term[@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [Dictionary/Acronyms/CasingExceptions/Acronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Dictionary\/Words\/Recognized\/Word  
 Per includere un termine nell'elenco di termini che l'analisi codice identifica come digitati correttamente, aggiungere il termine come testo interno di un elemento Dictionary\/Words\/Recognized\/Word.  Per i termini negli elementi Dictionary\/Words\/Recognized\/Word non viene fatta distinzione tra maiuscole e minuscole.  
  
 **Esempio**  
  
```  
<Dictionary>  
      <Words>  
         <Recognized>  
            <Word>knokker</Word>  
            ...  
         </Recognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Ai termini nei nodi Dictionary\/Words\/Recognized vengono applicate le regole di analisi codice seguenti:  
  
-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Dictionary\/Words\/Unrecognized\/Word  
 Per includere un termine nell'elenco di termini che l'analisi codice identifica come digitati correttamente, aggiungere il termine come testo interno di un elemento Dictionary\/Words\/Recognized\/Word.  Per i termini negli elementi Dictionary\/Words\/Unrecognized\/Word non viene fatta distinzione tra maiuscole e minuscole.  
  
 **Esempio**  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>meth</Word>  
            ...  
         </Unrecognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Ai termini nel nodo Dictionary\/Words\/Unrecognized vengono applicate le regole di analisi codice seguenti:  
  
-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionary\/Words\/Deprecated\/Term\[@PreferredAlternate\]  
 Per includere un termine nell'elenco di termini che l'analisi codice identifica come deprecati, aggiungere il termine come testo interno di un elemento Dictionary\/Words\/Recognized\/Word.  Un termine deprecato è una parola scritta correttamente, ma che non deve essere utilizzata.  
  
 Per includere un termine alternativo suggerito nell'avviso, specificare l'alternativa nell'attributo PreferredAlternate dell'elemento Term.  Se non si desidera suggerire un'alternativa, è possibile lasciare vuoto il valore dell'attributo.  
  
-   Per il termine deprecato nell'elemento Dictionary\/Words\/ Deprecated\/Term non viene fatta distinzione tra maiuscole e minuscole.  
  
-   Per il valore dell'attributo PreferredAlternate viene fatta distinzione tra maiuscole e minuscole.  Utilizzare la convenzione Pascal per le alternative composte.  
  
 **Esempio**  
  
```  
<Dictionary>  
      <Words>  
         <Deprecated>  
            <Term PreferredAlternate="LogOn">login</Term>  
            ...  
         </Deprecated>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Ai termini nel nodo Dictionary\/Words\/Deprecated vengono applicate le regole di analisi codice seguenti:  
  
-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary\/Words\/Compound\/Term\[@CompoundAlternate\]  
 Il dizionario incorporato identifica alcuni termini come singoli termini discreti, anziché come un termine composto.  Per includere un termine identificato come parola composta dall'analisi codice e specificare le maiuscole corrette di tale termine, aggiungere il termine come testo interno di un elemento Dictionary\/Words\/Compound\/Term.  Nell'attributo CompoundAlternate dell'elemento Term, specificare le singole parole che formano il termine composto, utilizzando la maiuscola per la prima lettera delle singole parole \(convenzione Pascal\).  Si noti che il termine specificato nel testo interno viene aggiunto automaticamente all'elenco Dictionary\/Words\/DiscreteExceptions.  
  
-   Per il termine deprecato nell'elemento Dictionary\/Words\/ Deprecated\/Term non viene fatta distinzione tra maiuscole e minuscole.  
  
-   Per il valore dell'attributo PreferredAlternate viene fatta distinzione tra maiuscole e minuscole.  Utilizzare la convenzione Pascal per le alternative composte.  
  
 **Esempio**  
  
```  
<Dictionary>  
      <Words>  
         <Compound>  
            <Term CompoundAlternate="CheckBox">checkbox</Term>  
            ...  
         </Compound>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Ai termini nel nodo Dictionary\/Words\/Compound vengono applicate le regole di analisi codice seguenti:  
  
-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary\/Words\/DiscreteExceptions\/Term  
 Per escludere un termine nell'elenco di termini che l'analisi codice identifica come singoli termini discreti, quando viene verificato se il termine soddisfa le regole di utilizzo delle maiuscole e minuscole per le parole composte, aggiungere il termine come testo interno di un elemento Dictionary\/Words\/DiscreteExceptions\/Term.  Per il termine deprecato nell'elemento Dictionary\/Words\/DiscreteExceptions\/Term non viene fatta distinzione tra maiuscole e minuscole.  
  
 **Esempio**  
  
```  
<Dictionary>  
      <Words>  
         <DiscreteExceptions>  
            <Term>checkbox</Term>  
            ...  
         </DiscreteExceptions>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Ai termini nel nodo Dictionary\/Words\/DiscreteExceptions vengono applicate le regole di analisi codice seguenti:  
  
-   [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Dictionary\/Acronyms\/CasingExceptions\/Acronym  
 Per includere un acronimo nell'elenco di termini che l'analisi codice identifica come digitati correttamente e per indicare l'acronimo quando viene verificato se il termine soddisfa le regole di utilizzo delle maiuscole e minuscole per le parole composte, aggiungere il termine come testo interno dell'elemento Dictionary\/Acronyms\/CasingExceptions\/Acronym.  Per l'acronimo nell'elemento Dictionary\/Acronyms\/CasingExceptions\/Acronym viene fatta distinzione tra maiuscole e minuscole.  
  
 **Esempio**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 Ai termini nel nodo Dictionary\/Acronyms\/CasingExceptions vengono applicate le regole di analisi codice seguenti:  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Per applicare un dizionario personalizzato a un progetto  
  
1.  In **Esplora soluzioni** utilizzare una delle procedure riportate di seguito:  
  
2.  Per aggiungere un dizionario a un singolo progetto, fare clic sul pulsante destro del mouse sul nome del progetto e scegliere **Aggiungi elemento esistente**.  Nella finestra di dialogo **Aggiungi elemento esistente** specificare il file.  
  
3.  Per aggiungere un dizionario condiviso fra due o più progetti, individuare il file da condividere nella finestra di dialogo **Aggiungi elemento esistente**, fare clic sulla freccia in giù sul pulsante **Aggiungi**, quindi fare clic su **Aggiungi come collegamento**.  
  
4.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome file **DizionarioPersonale.xml** e scegliere **Proprietà**.  
  
5.  Nell'elenco **Operazione di compilazione** selezionare **CodeAnalysisDictionary**.  
  
6.  Nell'elenco **Copia nella directory di output** selezionare **Non copiare**.