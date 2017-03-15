---
title: "Procedura dettagliata: Analisi del codice gestito per l&#39;identificazione di errori del codice | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analisi codice, procedure dettagliate"
  - "codice gestito, analisi"
  - "strumento di analisi del codice, procedure dettagliate"
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedura dettagliata: Analisi del codice gestito per l&#39;identificazione di errori del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata, verrà analizzato un progetto gestito per i difetti del codice utilizzando lo strumento di analisi codice.  
  
 Questa procedura dettagliata verrà descritte la procedura di utilizzo dell'analisi del codice per analizzare gli assembly di codice .NET gestito per conformità con le linee guida di progettazione di Microsoft .NET Framework.  
  
 In questa procedura dettagliata, è:  
  
-   Analizzare e risolvere gli avvisi degli errori di codice.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Creare una libreria di classi  
  
#### <a name="to-create-a-class-library"></a>Per creare una libreria di classi  
  
1.  Nel **File** dal menu di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], fare clic su **New** e quindi fare clic su **progetto**.  
  
2.  Nel **Nuovo progetto** nella finestra di dialogo **tipi di progetto**, fare clic su **Visual c#**.  
  
3.  In **modelli**, selezionare **libreria di classi**.  
  
4.  Nel **nome** nella casella di testo **CodeAnalysisManagedDemo** e quindi fare clic su **OK**.  
  
5.  Dopo aver creato il progetto, aprire il file Class1. cs.  
  
6.  Sostituire il testo esistente in Class1. cs con il codice seguente:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Salvare il file Class1. cs.  
  
## <a name="analyze-the-project"></a>Analizzare il progetto  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Per analizzare un progetto gestito per i difetti del codice  
  
1.  Selezionare il progetto CodeAnalysisManagedDemo in **Esplora**.  
  
2.  Nel **progetto** menu, fare clic su **proprietà**.  
  
     Verrà visualizzata la pagina di proprietà CodeAnalysisManagedDemo.  
  
3.  Fare clic su **CodeAnalysis**.  
  
4.  Assicurarsi che  **Attiva analisi codice in fase di compilazione (definisce la costante CODE_ANALYSIS**) sia selezionata.  
  
5.  Dal **eseguire il set di regole** elenco a discesa, selezionare **tutte le regole Microsoft**.  
  
6.  Nel **File** menu, fare clic su **Salva elementi selezionati**, e quindi chiudere le pagine delle proprietà ManagedDemo.  
  
7.  Nel **compilare** menu, fare clic su **Compila ManagedDemo**.  
  
     Vengono segnalati gli avvisi di compilazione progetto CodeAnalysisManagedDemo nel **analisi del codice** e **Output** windows.  
  
     Se il **analisi del codice** finestra non sono visualizzate, scegliere il **Analizza** menu, scegliere **Windows** e quindi **scegliere analisi del codice**.  
  
## <a name="correct-the-code-analysis-issues"></a>Correggere i problemi di analisi codice  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Per correggere le violazioni di regole di analisi codice  
  
1.  Nel **visualizzazione** menu, fare clic su **elenco errori**.  
  
     A seconda del profilo di sviluppo scelto, potrebbe essere necessario scegliere **altre finestre** sul **visualizzazione** menu e quindi fare clic su **elenco errori**.  
  
2.  In **Esplora**, fare clic su **Mostra tutti i file**.  
  
3.  Successivamente, espandere il nodo proprietà e quindi aprire il file AssemblyInfo.cs.  
  
4.  Per correggere gli avvisi, utilizzare il seguente:  
  
-   [CA1014: Contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: 'demo' deve essere contrassegnato con CLSCompliantAttribute e il relativo valore deve essere true.  
  
    -   Aggiungere il codice `using``System;` al file AssemblyInfo.cs.  
  
         Successivamente, aggiungere il codice `[assembly: CLSCompliant(true)]` alla fine del file AssemblyInfo.cs.  
  
         Ricompilare il progetto.  
  
-   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il costruttore seguente alla classe: public demo (String)  
  
    -   Aggiungere il costruttore `public demo (String s) : base(s) { }` alla classe `demo`.  
  
-   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il costruttore seguente alla classe: public demo (String, Exception)  
  
    -   Aggiungere il costruttore `public demo (String s, Exception e) : base(s, e) { }` alla classe `demo`.  
  
-   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il costruttore seguente alla classe: protected demo (SerializationInfo, StreamingContext)  
  
    -   Aggiungere il codice `using System.Runtime.Serialization;` all'inizio del file Class1. cs.  
  
         Successivamente, aggiungere il costruttore `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Ricompilare il progetto.  
  
-   [CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: aggiungere il costruttore seguente alla classe: public demo)  
  
    -   Aggiungere il costruttore `public demo () : base() { }` alla classe `demo`**.**  
  
         Ricompilare il progetto.  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere le maiuscole e minuscole del nome dello spazio dei nomi 'testCode' modificandolo in 'TestCode'.  
  
    -   Modifica le maiuscole e minuscole dello spazio dei nomi `testCode` a `TestCode`.  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere le maiuscole e minuscole nome del tipo 'demo' modificandolo in 'Demo'.  
  
    -   Modificare il nome del membro da `Demo`.  
  
-   [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: correggere le maiuscole e minuscole nome di membro 'item' modificandolo in 'Item'.  
  
    -   Modificare il nome del membro da `Item`.  
  
-   [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Naming: rinominare 'testCode.demo' per terminare con "Eccezione".  
  
    -   Modificare il nome della classe e i relativi costruttori in `DemoException`.  
  
-   [CA2210: Gli assembly devono avere nomi sicuri validi](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): firmare 'ManagedDemo' con una chiave con nome sicuro.  
  
    -   Nel **progetto** menu, fare clic su **proprietà ManagedDemo**.  
  
         Vengono visualizzate le proprietà del progetto.  
  
         Fare clic su **firma**.  
  
         Selezionare il **firmare l'assembly** casella di controllo.  
  
         Nel **scegliere un file chiave con nome** elenco, selezionare **\< nuovo >**.  
  
         Il **Crea chiave con nome sicuro** viene visualizzata la finestra di dialogo.  
  
         Nel **nome file di chiave**, digitare TestKey.  
  
         Immettere una password e quindi fare clic su **OK**.  
  
         Nel **File** menu, fare clic su **Salva elementi selezionati**, quindi chiudere le pagine delle proprietà.  
  
         Ricompilare il progetto.  
  
-   [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: aggiungere un attributo [Serializable] a 'demo' poiché questo tipo implementa ISerializable.  
  
    -   Aggiungere il `[Serializable ()]` attributo alla classe `demo`.  
  
         Ricompilare il progetto.  
  
 Dopo aver completato le modifiche, il file Class1. cs dovrebbe essere simile al seguente:  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
using System;  
using System.Runtime.Serialization;  
  
namespace TestCode  
{  
  
    [Serializable()]   
    public class DemoException : Exception  
    {  
        public DemoException () : base() { }  
        public DemoException(String s) : base(s) { }  
        public DemoException(String s, Exception e) : base(s, e) { }  
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }  
  
        public static void Initialize(int size) { }  
        protected static readonly int _item;  
        public static int Item { get { return _item; } }  
    }  
}  
```  
  
## <a name="exclude-code-analysis-warnings"></a>Escludere gli avvisi dell'analisi codice  
  
#### <a name="to-exclude-code-defect-warnings"></a>Per escludere gli avvisi degli errori di codice  
  
1.  Per ogni avviso rimanenti, procedere come segue:  
  
    1.  Nella finestra Analisi codice, selezionare l'avviso.  
  
    2.  Scegliere **azioni**, quindi scegliere **Elimina messaggio**, quindi scegliere **File di progetto eliminazione**.  
  
     Per ulteriori informazioni, vedere [procedura: esclusione di avvisi tramite la voce di Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Ricompilare il progetto.  
  
     Il progetto viene compilato senza avvisi o errori.