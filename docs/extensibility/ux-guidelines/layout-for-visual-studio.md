---
title: "Layout per Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Layout per Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La maggior parte delle finestre di dialogo di Visual Studio [Layout di finestra di dialogo utilità](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), che sono il unthemed finestre di dialogo standard di completamento [principi di layout di finestra di dialogo Windows Desktop](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx). Allo spostamento di Visual Studio aggiornare la relativa interfaccia utente, alcune delle finestre di dialogo più importante disporre di una nuova progettazione che stabilisce le esperienze di definizione prodotto. Queste [Layout della finestra di dialogo con tema](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) hanno un aspetto a tema.  
  
##  <a name="BKMK_UtilityDialogLayout"></a> Layout di finestra di dialogo utilità  
  
-   Tutti i controlli all'interno di una finestra di dialogo utilità dovrebbero iniziano l'angolo superiore sinistro e flusso verso il basso.  
  
-   Mai center controlli in una finestra di dialogo per riempire un'area di grandi dimensioni.  
  
-   Utilizzare il tipo di carattere ambiente per tutto il testo della finestra di dialogo. Quando si scrive una specifica visual, specificare il tipo di carattere ambiente invece di selezionare un particolare tipo di carattere e dimensioni. Vedere [Il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Utilizzare controllo coerente spaziatura e la selezione host per supportare l'obiettivo di qualità in fattura.  
  
-   Finestre di dialogo può diventare più complessi da un numero maggiore di controlli, un contatto univoco dei controlli o entrambi. Per tali situazioni complicate, consentire spazio sufficiente tra gruppi di controllo per consentire all'utente un flusso logico da analizzare.  
  
### Esempi di layout di finestra di dialogo utilità  
 Tutte le dimensioni sono espressi in pixel.  
  
 ![Dialog spacing for labels above controls](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801\-a\_UtilitySpacingAbove")  
  
 **Figura 08.01\-r: Spaziatura tra le linee guida per le finestre di dialogo utilità con etichette sopra i controlli**  
  
 ![Dialog spacing for labels to the left of controls](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801\-b\_UtilitySpacingLeft")  
  
 **Figura 08.01\-b: Spaziatura tra le linee guida per le finestre di dialogo utilità con etichette a sinistra dei controlli**  
  
### Dettagli di layout  
  
#### Margini  
  
-   Tutti i dialoghi devono avere un bordo di 12 pixel intorno ai lati.  
  
-   I margini all'interno di un gruppo devono essere 9 pixel dal bordo del frame.  
  
-   I margini all'interno di un controllo scheda devono essere 6 pixel dal bordo del controllo scheda.  
  
#### Pulsanti di comando  
  
-   Pulsanti di comando operano su frame finestra di dialogo, non sul contenuto. Che deve essere posizionati nella parte inferiore destra e deve disporre di sufficiente spazio variabile precedente per impostare i pulsanti separati.  
  
-   Se sono presenti pulsanti orizzontali che operano nella finestra di dialogo, la configurazione di pulsante di comando alternativo è uno stack verticale in alto a destra. Vedere [Pulsanti di comando interni](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) sotto.  
  
-   Lo spazio a sinistra dei pulsanti di comando \(inferiore a sinistra o al centro della finestra di dialogo\) viene considerato parte della "banda" dei controlli di finestra di dialogo operazione. L'unico elemento che deve comparire in tale spazio è un collegamento alla Guida che riguardano l'attività generale o la finestra di dialogo.  
  
-   Pulsanti di comando devono essere 75 x 23 pixel.  
  
-   Pulsanti di comando devono essere 6 pixel di distanza.  
  
 ![Basic button alignment](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801\-c\_ButtonAlign")  
  
 **Figura 08.01\-c: Allineamento di base dei pulsanti**  
  
#### Etichette  
  
-   Allinea a sinistra di tutte le etichette.  
  
-   Per le etichette che si trovano di sopra di un controllo, dovrebbe allineare a sinistra con precisione con il controllo sottostante e inferiore dell'etichetta deve essere di 5 pixel di sopra di altro controllo \(ad esempio, una casella combinata\).  
  
-   Per le etichette che si trovano a sinistra dei controlli, la larghezza minima tra l'etichetta e controllo di input è di 10 pixel. Stabilire una seconda colonna implicita per allineare le caselle di testo, caselle combinate o altri controlli.  
  
-   Le etichette sono normale e sono seguite da due punti. Vedere [Stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### Distanza tra i controlli  
 Stack ragionevolmente controlli. Non esiste alcun riferimento assoluto per la spaziatura tra i controlli in pila. Il livello tra i controlli può variare leggermente tra le finestre di dialogo. La spaziatura consigliata è 20 pixel per le coppie etichetta\/controllo verticale e 9 pixel per le coppie etichetta\/controllo orizzontale. La spaziatura minima di controlli per le coppie orizzontale è 6 pixel.  
  
 ![Recommended distance between controls](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801\-d\_ControlDistance")  
  
 **Figura 08.01\-d: Indicazioni per la distanza tra i controlli**  
  
#### Controllo rientro  
 Quando i controlli sono annidati, allineare i controlli interni orizzontalmente con il bordo sinistro del controllo precedente, in genere l'etichetta.  
  
 ![Nested control alignment](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801\-e\_ControlAlign")  
  
 **Figura 08.01\-e: Allineamento dei controlli annidati**  
  
#### Larghezza del controllo  
 La larghezza di una casella di testo o altri controlli simili deve essere non più di input medio per il campo. La parola inglese Media è di cinque caratteri. Ad esempio, una casella di testo che richiede un nome di percorso lungo deve essere purché consente il layout orizzontale, mentre un elenco a discesa per i nomi di piattaforma devono avere una lunghezza che consente la voce più lunga.  
  
#### Testo di supporto  
  
-   Una finestra di dialogo è possibile visualizzare il testo di supporto che fornisce ulteriori informazioni sullo scopo della finestra di dialogo. Questo in genere si trova nella parte superiore e può essere 1 o 2 frasi.  
  
-   La lunghezza di riga deve essere una larghezza comodo per un utente analizzare e leggere. Una finestra di dialogo medio deve essere non più di 550 pixel di larghezza.  
  
####  <a name="BKMK_InteriorCommandButtons"></a> Pulsanti di comando interni  
 Nelle finestre di dialogo più complesse, un controllo interno potrebbe essere proprio pulsanti correlati, che possono influire in cui si trovano i pulsanti di commit della finestra di dialogo.  
  
-   Utilizzare i pulsanti quando l'allineamento verticale \(colonna\) della parte interna **OK**\/**Annulla** orizzontalmente nell'angolo inferiore destro.  
  
-   Utilizzare i pulsanti quando l'allineamento orizzontale \(riga\) della parte interna **OK**\/**Annulla** sono orientati verticalmente in alto a destra. Questa situazione è meno comune.  
  
-   Dimensioni interni devono avere come destinazione le dimensioni del pulsante standard di 75 x 23 pixel, corrispondenti la dimensione di **OK**\/**Annulla** pulsanti quando possibile. Se un'etichetta rende il pulsante di superare le dimensioni del pulsante standard, gli altri pulsanti in tale set deve essere allineato con la dimensione più ampia.  
  
 ![Horizontal OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801\-f\_HorizOKCan")  
  
 **Figura 08.01\-f: Pulsanti verticale interno con OK\/Annulla orizzontale**  
  
 ![Vertical OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801\-g\_VertOKCan")  
  
 **Figura 08.01\-g: Pulsanti interni orizzontali con OK\/Annulla verticale**  
  
#### \[Sfoglia...\] button  
 **\[Sfoglia...\]** pulsanti che seguono una casella di testo devono spiegare chiaramente "Sfoglia..." in modo completo, inclusi i puntini di sospensione. Se lo spazio è insufficiente oppure sono presenti più **\[Sfoglia...\]** pulsanti sullo schermo, il pulsante possono essere ridotto a semplicemente i puntini di sospensione.  
  
##  <a name="BKMK_ThemedDialogLayout"></a> Layout della finestra di dialogo con tema  
 Finestre di dialogo temi di Visual Studio hanno un aspetto più chiaro e offrono ulteriori spazi vuoti. Tipografia fornisce maggiore enfasi e interesse, offrendo una variante di pesi e le dimensioni dei caratteri e interlinea più aperto. Dove possibile, le barre di colore e il titolo sono stati ridotte o rimosse. Il layout di queste finestre di dialogo deve seguire questo modello di base:  
  
1.  Lo sfondo della finestra di dialogo è bianco.  
  
2.  Esiste un bordo di 1 pixel regola in un valore medio di grigio.  
  
3.  Il titolo della finestra di dialogo non si trova in una barra del titolo, ma fornisce visual interesse ed enfasi un aumento delle dimensioni del punto. \(Vedere la sezione di dimensioni del carattere in [Stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).\)  
  
4.  Devono essere associate a un testo aggiuntivo, ad esempio una descrizione, le etichette **tipo di carattere ambiente \+ grassetto**.  
  
5.  Colonne interne sono separate da una regola di 1 pixel in grigio chiaro.  
  
6.  Collegamenti predefiniti non sono alcun carattere di sottolineatura. Al passaggio del mouse e premuti stati dispongono di una modifica del colore e carattere di sottolineatura.  
  
7.  Eseguire il commit i pulsanti \(ad esempio **OK**\/**Annulla**\) si trovano nell'angolo inferiore destro.  
  
### Esempi di layout di finestra di dialogo con tema  
 ![Themed dialog layout](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801\-h\_ThemedDialog")  
  
 **Figura 08.01\-h: Finestra di dialogo con tema**  
  
 ![Themed dialog dimensions](~/docs/extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801\-i\_ThemedDialogDimensions")  
  
 **Figura 08.01\-ricerca per categorie: Finestra di dialogo con tema: dimensioni**  
  
 ![Themed dialog fonts](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801\-j\_ThemedDialogFonts")  
  
 **Figura 08.01\-j: Finestra di dialogo con tema: i tipi di carattere**  
  
 ![Themed dialog colors](~/docs/extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801\-k\_ThemedDialogColors")  
  
 **Figura 08.01\-k Finestra di dialogo con tema: colori**  
  
## Vedere anche  
 [Modelli di applicazione per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Controlli \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [Finestre di dialogo \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)