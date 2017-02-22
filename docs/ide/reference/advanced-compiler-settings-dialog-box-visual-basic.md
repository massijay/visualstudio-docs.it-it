---
title: "Finestra di dialogo Impostazioni del compilatore avanzate (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAdvancedCompile"
helpviewer_keywords: 
  - "Finestra di dialogo Impostazioni del compilatore avanzate"
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 46
caps.handback.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Finestra di dialogo Impostazioni del compilatore avanzate (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La finestra di dialogo **Impostazioni del compilatore avanzate** di **Progettazione progetti** consente di specificare le proprietà avanzate di configurazione per la compilazione del progetto.  Questa finestra di dialogo si applica esclusivamente ai progetti di Visual Basic.  
  
### Per accedere a questa finestra di dialogo  
  
1.  In **Esplora soluzioni**, scegliere un nodo di progetto \(non il nodo **Soluzione** \).  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  In **Progettazione progetti** fare clic sulla scheda **Compila**.  
  
3.  In [Compilazione \(pagina\), Creazione progetti \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md) selezionare **Configurazione** e **Piattaforma**.  Nelle configurazioni di compilazione semplificate, gli elenchi **Configurazione** e **Piattaforma** non vengono visualizzati.  Per ulteriori informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e).  
  
4.  Fare clic su **Opzioni di compilazione avanzate**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Ottimizzazioni  
 Mediante le opzioni riportate di seguito vengono specificate ottimizzazioni che in alcuni casi possono ridurre le dimensioni di un programma, aumentarne la velocità di esecuzione o velocizzare il processo di compilazione.  
  
 **Rimuovi controllo dell'overflow di Integer**  
 Per impostazione predefinita, questa casella di controllo è deselezionata per abilitare il controllo dell'overflow di Integer.  Selezionare questa casella di controllo per rimuovere il controllo dell'overflow di Integer.  Se si seleziona questa casella di controllo, i calcoli Integer potrebbero essere più veloci.  Tuttavia, se si rimuove il controllo dell'overflow e un overflow delle capacità del tipo di dati, risultati errati vengano archiviati senza un errore generato.  
  
 Se le condizioni di overflow vengono archiviati e sovraccarichi Integer di un'operazione, viene generata un'eccezione di <xref:System.OverflowException> viene generata un'eccezione.  Se le condizioni di overflow non vengono archiviate, sovraccarichi Integer di operazione non generano un'eccezione.  
  
 **Attiva ottimizzazioni**  
 Per impostazione predefinita, questa casella di controllo è deselezionata per disabilitare le ottimizzazioni del compilatore.  Selezionare questa casella di controllo per attivare le ottimizzazioni del compilatore.  Le ottimizzazioni del compilatore consentono di ridurre le dimensioni del file di output e di renderlo più veloce e più efficiente.  Tuttavia, poiché la ridisposizione nel file di output, ottimizzazioni del compilatore di codice causa di ottimizzazioni può rendere più difficile il debug.  
  
 **Indirizzo di base DLL**  
 In questa casella di testo viene visualizzato l'indirizzo di base DLL predefinito in formato esadecimale.  Nei progetti Libreria di classi e Libreria di Controllo, è possibile utilizzare questa casella di testo per specificare l'indirizzo di base da utilizzare quando viene creata la DLL.  
  
 **Genera informazioni di debug**  
 Selezionare **None**, **Full** o **pdb\-only** dall'elenco.  **None** specifica che non saranno generate informazioni di debug.  **Full** specifica che verranno generate informazioni di debug complete e **pdb\-only** specifica che verranno generate solo informazioni di debug PDB.  Per impostazione predefinita, questa opzione è impostata su **Full**.  
  
## Costanti di compilazione  
 Le costanti di compilazione condizionale hanno un effetto simile a quello di utilizzare una direttiva per il preprocessore di [\#Const](/dotnet/visual-basic/language-reference/directives/const-directive) in un file di origine, ad eccezione delle costanti definite sono pubbliche e si applicano a tutti i file nel progetto.  È possibile utilizzare le costanti di compilazione condizionale con la direttiva di [\#Else \#If… Quindi…](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) per la compilazione condizionale i file di origine.  Vedere [Conditional Compilation](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).  
  
 **Definisci costante DEBUG**  
 Per impostazione predefinita, questa casella di controllo è selezionata e specifica che deve essere impostata una costante DEBUG.  
  
 **Definisci costante TRACE**  
 Per impostazione predefinita, questa casella di controllo è selezionata e specifica che verrà impostata una costante TRACE.  
  
 **Costanti personalizzate**  
 Immettere qualsiasi costante personalizzata per l'applicazione in questa casella di testo.  Le voci devono essere delimitate da virgole, nel seguente formato: Nome1\="Valore1",Nome2\="Valore2",Nome3\="Valore3".  
  
## Altre impostazioni  
 **Genera assembly di serializzazione**  
 Questa impostazione specifica se il compilatore creerà assembly di serializzazione XML.  Gli assembly di serializzazione possono migliorare le prestazioni di avvio della classe <xref:System.Xml.Serialization.XmlSerializer>, se è stata utilizzata per serializzare tipi nel codice.  Per impostazione predefinita, questa opzione è impostata su **Auto**, che specifica che verranno generati assembly di serializzazione solo se è stata utilizzata la classe <xref:System.Xml.Serialization.XmlSerializer> per codificare tipi nel codice in XML.  **Off** specifica che non verranno mai generati assembly di serializzazione, indipendentemente dal fatto che il codice utilizzi la classe <xref:System.Xml.Serialization.XmlSerializer> o meno.  **On** specifica che verranno sempre generati assembly di serializzazione.  Gli assembly di serializzazione sono denominati `TypeName`.XmlSerializers.dll.  
  
## Vedere anche  
 [Compilazione \(pagina\), Creazione progetti \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)