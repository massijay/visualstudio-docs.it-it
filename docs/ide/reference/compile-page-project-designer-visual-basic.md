---
title: "Compilazione (pagina), Creazione progetti (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesCompile"
helpviewer_keywords: 
  - "compilazione, progetti Visual Basic"
  - "compilazione, opzioni [Visual Basic]"
  - "compilatori, opzioni di Visual Basic"
  - "compilazione, istruzioni [Visual Basic]"
  - "opzioni del compilatore, Visual Basic"
  - "Creazione progetti, pagina Compilazione"
  - "Compilazione (pagina) in Creazione progetti"
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# Compilazione (pagina), Creazione progetti (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La pagina **Compila** di Progettazione progetti consente di specificare le istruzioni di compilazione.  Consente anche di specificare opzioni avanzate del compilatore ed eventi pre\-compilazione o post\-compilazione.  
  
 Per accedere alla pagina **Compilazione**, scegliere un nodo di progetto \(non il nodo **Soluzione** \) in **Esplora soluzioni**.  Scegliere **Progetto**, **Proprietà** sulla barra dei menu.  In Progettazione progetti fare clic sulla scheda **Compila**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Configurazione e piattaforma  
 Le seguenti impostazioni consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.  
  
> [!NOTE]
>  Con configurazioni della build semplificate, il sistema del progetto determina se compilare una versione di debug o di rilascio.  Pertanto, gli elenchi **Configurazione** e **Piattaforma** non vengono visualizzati.  Per ulteriori informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e).  
  
 **Configurazione**  
 Specifica le impostazioni di configurazione da visualizzare o modificare.  Le impostazioni sono **Debug** \(impostazione predefinita\), **Release**o **Tutte le configurazioni**.  Per ulteriori informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e) e [Procedura: creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md).  
  
 **Piattaforma**  
 Specifica le impostazioni della piattaforma da visualizzare o modificare.  È possibile specificare **Qualsiasi CPU** \(impostazione predefinita\), **x64**, o **x86**.  Per ulteriori informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e).  
  
## Opzioni di configurazione del compilatore  
 Le impostazioni riportate di seguito consentono di definire le opzioni di configurazione del compilatore.  
  
 **Percorso dell'output di compilazione**  
 Specifica il percorso dei file di output per la configurazione del progetto.  Digitare il percorso dell'output di compilazione in questa casella oppure scegliere il pulsante **Sfoglia** per selezionare un percorso.  Questo percorso è relativo. Se si immette un percorso assoluto verrà salvato come relativo.  Il percorso predefinito è bin\\Debug\\ o bin\\Release\\.  Per ulteriori informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e).  
  
 Con configurazioni della build semplificate, il sistema del progetto determina se compilare una versione di debug o di rilascio.  Scegliendo **Compilazione** dal menu **Debug** \(F5\) la compilazione verrà collocata nel percorso di debug indipendentemente dal **Percorso output** specificato.  Tuttavia, il comando **Compila** dal menu **Compila** la inserisce nel percorso specificato.  Per ulteriori informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e).  
  
 **Option explicit**  
 Specifica se consentire la dichiarazione implicita delle variabili.  Selezionare **Attivo** per richiedere la dichiarazione esplicita delle variabili.  Ciò determina la segnalazione di errori nel compilatore se le variabili non vengono dichiarate prima di essere utilizzate.  Selezionare **Off** per consentire la dichiarazione implicita delle variabili.  
  
 Questa impostazione corrisponde all'opzione del compilatore [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 Se un file di codice sorgente contiene [Option Explicit Statement](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), il valore `On` o `Off` nell'istruzione esegue l'override dell'impostazione **Option Explicit** nella **pagina Compila**.  
  
 Quando si crea un nuovo progetto, l'impostazione **Option Explicit** nella pagina **Compila** viene definita in base al valore dell'impostazione **Option Explicit** della finestra di dialogo **Opzioni**.  Per visualizzare o modificare l'impostazione di questa finestra di dialogo dal menu **Strumenti**, scegliere **Opzioni**.  Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**.  L'impostazione predefinita iniziale di **Option Explicit** in **Impostazioni predefinite di Visual Basic** è **On**.  
  
 L'impostazione di **Option Explicit** su `Off` in genere non è consigliabile.  L'ortografia di un nome di variabile in uno o più i percorsi potrebbe essere errata e generare, in tal modo, risultati imprevisti quando viene eseguito il programma.  
  
 **Option strict**  
 Specifica se applicare la semantica dei tipi rigorosa.  Quando **Option Strict** è impostato su **On**, le condizioni riportate di seguito generano un errore in fase di compilazione:  
  
-   Conversioni di restrizione implicite  
  
-   Associazione tardiva  
  
-   Tipizzazione implicita che risulta in un tipo `Object`  
  
 Gli errori di conversione di restrizione implicita si verificano quando esiste una conversione di tipo di dati implicita che è una conversione di restrizione.  Per ulteriori informazioni, vedere [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) e [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).  
  
 Oggetto è associato tardivamente quando è assegnato a una proprietà o a un metodo di una variabile dichiarata di tipo `Object`.  Per ulteriori informazioni, vedere [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement) e [Early and Late Binding](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding).  
  
 Gli errori del tipo di oggetti impliciti si verificano quando non può essere derivato un tipo appropriato per una variabile dichiarata, in modo da derivare un tipo di `Object`.  Ciò principalmente si verifica quando si utilizza un'istruzione `Dim` per dichiarare una variabile senza utilizzare una clausola `As` e `Option Infer` non è attivo.  Per ulteriori informazioni, vedere [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement) e [Visual Basic Language Specification](/dotnet/visual-basic/reference/language-specification).  
  
 L'impostazione **Option Strict** corrisponde all'opzione del compilatore [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 Se un file di codice sorgente contiene [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), il valore `On` o `Off` nell'istruzione esegue l'override dell'impostazione **Option Strict** nella **pagina Compila**.  
  
 Quando si crea un progetto, l'impostazione **Option Strict** nella **pagina Compila** viene impostata con il valore dell'impostazione **Option Strict** della finestra di dialogo **Opzioni**.  Per visualizzare o modificare l'impostazione di questa finestra di dialogo dal menu **Strumenti**, scegliere **Opzioni**.  Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**.  L'impostazione predefinita iniziale di **Option Strict** in **Impostazioni predefinite di Visual Basic** è **Off**.  
  
 **Avvisi singoli di Option Strict.** La sezione **Configurazioni avvisi** della pagina **Compilazione** ha impostazioni che corrispondono alle tre condizioni che generano un errore in fase di compilazione quando `Option Strict` è attivata.  Di seguito sono riportate queste impostazioni:  
  
-   **Conversione implicita**  
  
-   **Associazione tardiva; la chiamata potrebbe avere esito negativo in fase di esecuzione**  
  
-   **Tipo implicito: presunto oggetto**  
  
 Quando si imposta **Option Strict** su **On**, le tre impostazioni di configurazione di avviso vengono impostate su **Error**.  Quando si imposta **Option Strict** su **Off**, tutte e tre le impostazioni vengono impostate su **None**.  
  
 È possibile modificare singolarmente ogni impostazione di configurazione dell'avviso su **None**, **Warning**, o **Error**.  Se tutte e tre le impostazioni di configurazione di avviso sono impostate su **Errore**, `On` verrà visualizzato nella casella `Option strict`.  Se tutti e tre sono impostati su **Nessuno**, `Off` sarà visualizzato in questa casella.  Per qualsiasi altra combinazione di queste impostazioni, **\(custom\)** è visualizzata.  
  
 **Option compare**  
 Specifica il tipo di confronto tra stringhe da utilizzare.  Selezionare **Binary** per indicare al compilatore di utilizzare confronti tra stringhe binari con distinzione tra maiuscole e minuscole.  Scegliere **Text** per utilizzare confronti tra stringhe di testo specifici delle impostazioni locali senza distinzione tra maiuscole e minuscole.  
  
 Questa impostazione corrisponde all'opzione del compilatore [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 Se un file di codice sorgente contiene [Option Compare Statement](/dotnet/visual-basic/language-reference/statements/option-compare-statement), il valore `Binary` o `Text` nell'istruzione esegue l'override dell'impostazione **Option Compare** nella **pagina Compila**.  
  
 Quando si crea un progetto, l'impostazione **Option Compare** nella **pagina Compila** viene impostata con il valore dell'impostazione **Option Compare** della finestra di dialogo **Opzioni**.  Per visualizzare o modificare l'impostazione di questa finestra di dialogo dal menu **Strumenti**, scegliere **Opzioni**.  Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**.  L'impostazione predefinita iniziale in **Option Compare** in **Impostazioni predefinite di Visual Basic** è **Binario**.  
  
 **Option Infer**  
 Specifica se consentire l’inferenza di tipo locale nelle dichiarazioni delle variabili.  Selezionare **Attivo** per consentire l'utilizzo dell'inferenza del tipo di variabile locale.  Selezionare **Off** per bloccare l’inferenza di tipo locale.  
  
 Questa impostazione corrisponde all'opzione del compilatore [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
 Se un file di codice sorgente contiene [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement), il valore `On` o `Off` nell'istruzione esegue l'override dell'impostazione **Option Infer** nella **pagina Compila**.  
  
 Quando si crea un progetto, l'impostazione **Option Infer** nella **pagina Compila** viene impostata con il valore dell'impostazione **Option Infer** della finestra di dialogo **Opzioni**.  Per visualizzare o modificare l'impostazione di questa finestra di dialogo dal menu **Strumenti**, scegliere **Opzioni**.  Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**.  L'impostazione predefinita iniziale di **Option Infer** in **Impostazioni predefinite di Visual Basic** è **On**.  
  
 **CPU di destinazione**  
 Specifica il processore di destinazione del file di output.  Specificare **x86** per il processore intel compatibile a 32 bit, **x64** per ogni processore intel compatibile a 64 bit, **ARM** per il processore di ARM, o **Qualsiasi CPU** per specificare che un processore è accettabile.  **Qualsiasi CPU** è il valore predefinito per i nuovi progetti in quanto consente l'applicazione in gran numero dei tipi hardware.  
  
 Per ulteriori informazioni, vedere [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
 **Preferisci 32 bit**  
 Se la casella di controllo **Prefer32\-bit** è selezionata, l'applicazione viene eseguita come applicazione a 32 bit e a 32 bit nelle versioni a 64 bit di Windows.  In caso contrario, l'applicazione viene eseguito come un'applicazione a 32 bit su versioni a 32 bit di Windows e come applicazione a 64 bit su versioni a 64 bit di Windows.  
  
 Viene eseguito come un'applicazione a 64 bit raddoppia la dimensione del puntatore e possono causare problemi di compatibilità con le librerie che sono disponibili separatamente 32 bit.  È opportuno eseguire un'applicazione a 64 bit solo se viene eseguito molto più velocemente o necessita più di 4 GB di memoria.  
  
 Questa casella di controllo è disponibile solo se tutte le condizioni seguenti sono vere:  
  
-   In **Compila pagina**, l'elenco **CPU di destinazione** è impostato su **Qualsiasi CPU**.  
  
-   In **Pagina applicazione**, l'elenco **Tipo di applicazione** specifica che il progetto è un'applicazione.  
  
-   In **Pagina applicazione**, l'elenco **Framework di destinazione** specifica .NET Framework 4,5.  
  
 **Configurazioni avvisi**  
 In questa tabella sono elencate le condizioni di compilazione e il corrispondente livello di notifica, **Nessuno**, **Avviso** o **Errore**.  
  
 Per impostazione predefinita, tutti gli avvisi del compilatore vengono aggiunti all'Elenco attività durante la compilazione.  Selezionare **Disabilita tutti gli avvisi** per indicare al compilatore di non generare avvisi o errori.  Selezionare **Considera tutti gli avvisi come errori** se si desidera che gli avvisi vengano considerati come errori da correggere.  
  
 **Disabilita tutti gli avvisi**  
 Specifica se consentire al compilatore di generare notifiche come specificato nella tabella **Condizione e notifica** descritta precedentemente in questo documento.  Per impostazione predefinita, questa casella di controllo è deselezionata.  Selezionare questa casella di controllo per indicare al compilatore di non generare avvisi o errori.  
  
 Questa impostazione corrisponde all'opzione del compilatore [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
 **Considera tutti gli avvisi come errori**  
 Specifica come considerare gli avvisi.  Per impostazione predefinita questa casella di controllo è deselezionata, pertanto tutte le notifiche di avviso sono impostate su **Avviso**.  Selezionare questa casella di controllo per impostare tutte le notifiche di avviso su **Errore**.  
  
 Questa opzione è disponibile solo se la casella di controllo **Disabilita tutti gli avvisi** è deselezionata.  
  
 **Genera il file di documentazione XML**  
 Specifica se generare le informazioni di documentazione.  Per impostazione predefinita questa casella di controllo è selezionata, per indicare al compilatore di generare le informazioni di documentazione e inserirle in un file XML.  Deselezionare questa casella di controllo per indicare al compilatore di non creare la documentazione.  
  
 Questa impostazione corrisponde all'opzione del compilatore [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).  
  
 **Registra per interoperabilità COM**  
 Specifica se l'applicazione gestita esporrà un oggetto COM \(un COM\-callable wrapper\) che consente a un oggetto COM di interagire con l'applicazione.  
  
 Per impostazione predefinita questa casella di controllo è deselezionata, per specificare che l'applicazione non consentirà l'interoperabilità COM.  Selezionare questa casella di controllo per consentire l'interoperabilità COM.  
  
 Questa opzione non è disponibile per progetti Applicazione Windows o Applicazione console.  
  
 **Eventi di compilazione**  
 Fare clic su questo pulsante per accedere alla finestra di dialogo **Eventi di compilazione**.  Utilizzare questa finestra di dialogo per specificare le istruzioni di configurazione di pre\-compilazione e post\-compilazione per il progetto.  Questa finestra di dialogo si applica esclusivamente ai progetti di Visual Basic.  Per ulteriori informazioni, vedere [Finestra di dialogo Eventi di compilazione \(Visual Basic\)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
 **Opzioni di compilazione avanzate**  
 Fare clic su questo pulsante per accedere alla finestra di dialogo **Impostazioni del compilatore avanzate**.  Utilizzare la finestra di dialogo **Impostazioni del compilatore avanzate** per specificare le proprietà avanzate di configurazione della build del progetto.  Questa finestra di dialogo si applica esclusivamente ai progetti di Visual Basic.  Per ulteriori informazioni, vedere [Finestra di dialogo Impostazioni del compilatore avanzate \(Visual Basic\)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## Vedere anche  
 [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e)   
 [Managing Compilation Properties](http://msdn.microsoft.com/it-it/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Procedura: specificare gli eventi di compilazione \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Procedura: creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md)