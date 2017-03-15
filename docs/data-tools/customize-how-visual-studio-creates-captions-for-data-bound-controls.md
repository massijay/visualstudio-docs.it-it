---
title: "Procedura: personalizzare la modalit&#224; in cui in Visual Studio vengono create didascalie per controlli con associazione a dati | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "didascalie, associate a dati"
  - "Origini dati (finestra), didascalie di etichetta"
  - "didascalie di etichetta, Origini dati (finestra)"
  - "Smart (didascalie)"
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: personalizzare la modalit&#224; in cui in Visual Studio vengono create didascalie per controlli con associazione a dati
Quando si esegue il trascinamento di elementi dalla [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md) in Progettazione Windows Form, è opportuno tenere presente che in presenza di due o più parole concatenate, i nomi di colonna nelle etichette della didascalia vengono riformattati in stringhe di più semplice lettura.  È possibile personalizzare la modalità di creazione di queste etichette impostando i valori di **SmartCaptionExpression**, **SmartCaptionReplacement** e **SmartCaptionSuffix** sulla chiave del Registro di sistema **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\Data Designers**.  
  
> [!NOTE]
>  Questa chiave del Registro di sistema non esiste finché non viene creata.  
  
 La didascalia smart è controllata dall'espressione regolare immessa all'interno del valore **SmartCaptionExpression**.  Aggiungendo la chiave del Registro di sistema **Data Designers**, viene eseguito l'override dell'espressione regolare predefinita che controlla le etichette di didascalia.  Per ulteriori informazioni sulle espressioni regolari, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Nella tabella seguente vengono descritti i valori del Registro di sistema che controllano le etichette di didascalia.  
  
|Elemento del Registro di sistema|Descrizione|  
|--------------------------------------|-----------------|  
|SmartCaptionExpression|Espressione regolare utilizzata per il confronto dei modelli personalizzati.|  
|SmartCaptionReplacement|Formato di visualizzazione delle corrispondenze dei gruppi all'interno di **SmartCaptionExpression**.|  
|SmartCaptionSuffix|Stringa opzionale da aggiungere alla fine della didascalia.|  
  
 Nelle tabelle seguenti vengono elencate le impostazioni predefinite interne per questi valori del Registro di sistema.  
  
|Elemento|Valore predefinito|Descrizione|  
|--------------|------------------------|-----------------|  
|**SmartCaptionExpression**|\(\\\\p{Ll}\)\(\\\\p{Lu}\)&#124;\_\+|Corrisponde a un carattere minuscolo seguito da un carattere maiuscolo oppure da un trattino di sottolineatura.|  
|**SmartCaptionReplacement**|$1 $2|$1 rappresenta i caratteri di cui è stata rilevata la corrispondenza nella prima parentesi dell'espressione mentre il carattere $2 rappresenta i caratteri di cui è stata rilevata la corrispondenza nella seconda parentesi.  La sostituzione è la prima corrispondenza, uno spazio e, successivamente, la seconda corrispondenza.|  
|**SmartCaptionSuffix**|:|Rappresenta un carattere aggiunto alla stringa restituita.  Ad esempio, se la didascalia è `Company Name`, il suffisso la trasforma in `Company Name:`|  
  
> [!CAUTION]
>  Prestare particolare attenzione nell'esecuzione di qualsiasi azione nell'Editor del Registro di sistema.  Creare una copia di backup del Registro di sistema prima di modificarlo.  L'utilizzo non corretto dell'Editor del Registro di sistema può causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo.  Microsoft non garantisce la risoluzione dei problemi causati dall'utilizzo non corretto dell'Editor del Registro di sistema.  Utilizzare l'Editor del Registro di sistema sotto la propria responsabilità.  
>   
>  L'articolo della KnowledgeBase riportato di seguito contiene istruzioni per eseguire il backup, la modifica e il ripristino del Registro di sistema: [Descrizione del Registro di sistema di Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) \(http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;256986\)  
  
### Per modificare il comportamento della didascalia smart della finestra Origini dati.  
  
1.  Aprire una finestra di comando facendo clic su **Start** e quindi su **Esegui**.  
  
2.  Digitare `regedit` nella finestra di dialogo **Esegui** e scegliere **OK**.  
  
3.  Espandere il nodo **HKEY\_CURRENT\_USER**.  
  
4.  Espandere il nodo **Software**.  
  
5.  Espandere il nodo **Microsoft**.  
  
6.  Espandere il nodo **VisualStudio**.  
  
7.  Fare clic con il pulsante destro del mouse sul nodo **10.0** e creare una nuova **Chiave** denominata `Data Designers`.  
  
8.  Fare clic con il pulsante destro del mouse sul nodo **Data Designers** e creare un nuovo **Valore stringa** denominato `SmartCaptionExpression`.  
  
9. Fare clic con il pulsante destro del mouse sul nodo **Data Designers** e creare un nuovo **Valore stringa** denominato `SmartCaptionReplacement`.  
  
10. Fare clic con il pulsante destro del mouse sul nodo **Data Designers** e creare un nuovo **Valore stringa** denominato `SmartCaptionSuffix`.  
  
11. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionExpression** e scegliere **Modifica**.  
  
12. Immettere l'espressione regolare da utilizzare nella finestra **Origini dati**.  
  
13. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionReplacement** e scegliere **Modifica**.  
  
14. Immettere la stringa di sostituzione formattata nella modo scelto per la visualizzazione dei modelli di cui si è rilevata la corrispondenza nell'espressione regolare in uso.  
  
15. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionSuffix** e scegliere **Modifica**.  
  
16. Immettere il carattere da visualizzare alla fine della didascalia.  
  
     Nel successivo trascinamento degli elementi dalla finestra **Origini dati**, le etichette della didascalia verranno create utilizzando i nuovi valori del Registro di sistema forniti.  
  
### Per disattivare la funzionalità di didascalia smart  
  
1.  Aprire una finestra di comando facendo clic su **Start** e quindi su **Esegui**.  
  
2.  Digitare `regedit` nella finestra di dialogo **Esegui** e scegliere **OK**.  
  
3.  Espandere il nodo **HKEY\_CURRENT\_USER**.  
  
4.  Espandere il nodo **Software**.  
  
5.  Espandere il nodo **Microsoft**.  
  
6.  Espandere il nodo **VisualStudio**.  
  
7.  Fare clic con il pulsante destro del mouse sul nodo **10.0** e creare una nuova **Chiave** denominata `Data Designers`.  
  
8.  Fare clic con il pulsante destro del mouse sul nodo **Data Designers** e creare un nuovo **Valore stringa** denominato `SmartCaptionExpression`.  
  
9. Fare clic con il pulsante destro del mouse sul nodo **Data Designers** e creare un nuovo **Valore stringa** denominato `SmartCaptionReplacement`.  
  
10. Fare clic con il pulsante destro del mouse sul nodo **Data Designers** e creare un nuovo **Valore stringa** denominato `SmartCaptionSuffix`.  
  
11. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionExpression** e scegliere **Modifica**.  
  
12. Immettere `(.*)` per il valore.  Tale procedura determinerà la corrispondenza dell'intera stringa.  
  
13. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionReplacement** e scegliere **Modifica**.  
  
14. Immettere `$1` per il valore.  Tale procedura sostituisce la stringa con il valore di cui si è determinata la corrispondenza, che rappresenta l'intera stringa in modo da restare invariato.  
  
     Nel successivo trascinamento degli elementi dalla finestra **Origini dati**, le etichette della didascalia verranno create con didascalie non modificate.  
  
## Vedere anche  
 [Espressioni regolari di .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)