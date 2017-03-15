---
title: "Strumenti di valutazione per Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# Strumenti di valutazione per Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Elenco di controllo maestria per Visual Studio  
 Utilizzare questo elenco di controllo per la valutazione di qualità di esperienza utente per informazioni dettagliate di visual e interazione.  
  
### Panoramica  
  
-   Verificare che tutti i comandi generi commenti e suggerimenti che indica agli utenti che sono stati effettuati i relativi comandi.  
  
-   Verificare che tutti gli elementi dell'interfaccia utente e i controlli siano visibili in tutti i temi e in modalità a contrasto elevato.  
  
-   Verificare che inattiva e attiva la selezione si differenziano sempre, sia in modalità contrasto elevato e standard.  
  
-   Verificare che lo stato attivo è sempre visibile e apparente.  
  
### Prestazioni  
  
-   Verificare che alcuni indicatore del tipo di "occupato" viene visualizzato se un comando ha più di un secondo per il completamento.  
  
-   Verificare che se un comando richiede più di 10 secondi per completare un indicatore di stato esplicito, ovvero determinata \(scelta consigliata\) o indeterminato, viene visualizzato.  
  
### Testo dell'interfaccia utente  
  
-   Verificare che tutte le etichette siano frase o maiuscolo e che il testo non è completamente lettere minuscolo.  
  
    ||Correggere|Non corretto|  
    |-|----------------|------------------|  
    |**Testo del comando \(tutti\)**|Normale:<br /><br /> **Nome della directory:**|Nome della directory:|  
    |**Testo del pulsante \(client\)**|Iniziali maiuscole:<br /><br /> **\[Predefinito\]**|SET AS DEFAULT|  
    |**Testo del pulsante \(online\)**|Normale:<br /><br /> **\[Impostazione predefinita\]**||  
  
-   Verificare che tutte le etichette, ad eccezione di intestazioni di gruppo e i pulsanti, terminano con un virgola e precedono il controllo con cui vengono combinati.  
  
-   Verificare che i pulsanti, comandi e collegamenti ai comandi di avvio dell'interfaccia utente per acquisire l'input dell'utente terminare con i puntini di sospensione **\[…\]**.  
  
     Esempi:  
  
    -   Un **\[avanzate...\]** pulsante in una finestra di dialogo.  
  
    -   Le opzioni di comando del menu Strumenti \(**Strumenti \> Opzioni**\) devono ottenere i puntini di sospensione, perché l'avvio la finestra di dialogo è lo scopo del comando.  
  
-   Verificare che l'interfaccia utente non contiene abbreviazioni, ad eccezione di termini standard del settore. Ad esempio, HTML né TCP\/IP necessario pronunciata, se deve insufficiente \(esaurito la memoria\) e informazioni personali \(informazioni personali\).  
  
### Accesso da tastiera  
  
-   Verificare che vi sia un modo per eseguire ogni attività con la tastiera. In genere questa operazione viene eseguita tramite l'accesso da tastiera per ogni controllo, ma per alcune aree impatto visivo, risolvere il problema, ad esempio passando alla visualizzazione del codice è accettabile.  
  
-   Verificare che è possibile scheda tramite i controlli in un ordine logico \(da sinistra a destra e dall'alto in basso\). Si tratta di una procedura consigliata per la maggior parte dei controlli, non tutti i controlli richiedono questo approccio. Ad esempio, verificare il pulsante di opzione sono controlli in un gruppo con una singola tabulazione.  
  
-   Verificare che tutti i controlli dispongono di etichette e che ogni etichetta disponga di un tasto di scelta rapida \(eccezioni includono alcuni controlli con etichetta non potrebbero seguire un controllo etichettato nella scheda\).  
  
-   Verificare che non sono presenti conflitti di tasti di scelta rapida.  
  
### Tipi di carattere  
  
-   Verificare che tutti i tipi di carattere \(carattere, dimensione, colore\) vengono utilizzati in modo coerente e mantenere la gerarchia.  
  
-   Verificare che tutti gli elementi dell'interfaccia utente utilizzano il servizio di tipo di carattere ambiente. \(Vedere [I tipi di carattere e la formattazione per Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)\)  
  
     Per verificare se il servizio è in uso, passare a **Strumenti \> Opzioni \> tipi di carattere e colori**. Nell'elenco a discesa delle impostazioni, scegliere tipo di carattere ambiente e modificare il tipo di carattere a un elemento stylistically diverso \(ad esempio Harrington o fumetti SAN\) e impostare le dimensioni a 12 punti. Fare clic su OK. Potrebbe essere necessario riavviare l'IDE, ma la maggior parte dell'interfaccia utente verrà modificato immediatamente. Le aree che non rileverà la modifica del tipo di carattere anche al riavvio non si utilizzano il tipo di carattere ambiente.  
  
-   Verificare che i tipi di carattere derivato del servizio \(ad esempio, testo in grassetto o ingrandito\) mantenuto le dimensioni e la formattazione in relazione al testo "normale" quando viene modificata la dimensione del carattere di ambiente.  
  
-   Verificare che siano non disponibili sono presenti errori ritaglio a causa di tipi di carattere ingranditi. I tipi di carattere bloccarsi sono probabilmente il risultato dei controlli di altezza fissa o contenitori altezza fissa.  
  
### Finestre di dialogo  
  
-   Verificare che il titolo della finestra di comando che l'ha avviata.  
  
-   Verificare che tutti i controlli standard sono coerenti con il sistema operativo: colore di sfondo è standard e nessun controllo deve disporre di uno stile basato su modelli re speciale che rende diverso dai controlli standard.  
  
-   Verificare che i margini all'interno del form devono essere 12 pixel e risulterà uniforme e coerente.  
  
-   Verificare che appaiano centrati all'interno di shell IDE o nella finestra che ha generato le finestre di dialogo.  
  
-   Quando si rivela utile, finestre di dialogo possono essere ridimensionati. Per i dialoghi che sono ridimensionabili, verificare che al momento del ridimensionamento, necessario ridimensionare i controlli appropriati mentre le altre parti della finestra di dialogo rimangono costanti.  
  
-   Verificare che le finestre di dialogo ridimensionabile rendere persistente qualsiasi dimensione regolare utente \(dimensioni, il percorso, l'espansione dei controlli di finestra di dialogo e così via\).  
  
-   Verificare che non sia visualizzata alcuna icona nella barra del titolo.  
  
-   Verificare che non sono presenti pulsanti di ingrandimento e riduzione a icona nella barra del titolo.  
  
#### Pulsanti di operazione di finestra di dialogo \(solo Client di Visual Studio\)  
  
-   Verificare che i pulsanti di operazione in questo ordine: **OK**, **Annulla**, **Applica**.  
  
-   Verificare che **OK** e **Annulla** pulsanti sono le dimensioni standard: 75 x 23 pixel.  
  
-   Verificare che **OK** e **Annulla** pulsanti sono della stessa dimensione indipendentemente dalla lunghezza della stringa.  
  
-   Se l'etichetta su un pulsante operazione richiede il pulsante deve essere maggiore di standard, verificare che il corrispondente **Annulla** pulsante è di dimensioni uguali.  
  
-   Verificare che vi sia un riempimento 6 pixel tra i pulsanti e i controlli associati.  
  
-   Verificare che il **OK** e **Annulla** pulsanti non hanno tasti di accesso definito da una lettera sottolineata.  
  
-   Verificare che un pulsante \(in genere **OK**\) ha lo stato attivo per impostazione predefinita.  
  
-   Verificare che **Esc** Annulla la finestra di dialogo  
  
-   Verificare che **INVIO** esegue il pulsante predefinito, se lo stato attivo non è presente in un controllo che elabora l'invio.  
  
-   Verificare che il **OK** e **Annulla** pulsanti sono posizionati nell'angolo inferiore destro della finestra di dialogo. In rare eccezioni, è accettabile per poter essere sovrapposti in verticale in alto a destra.  
  
-   Verificare che la configurazione verticale viene utilizzata solo se sono presenti altri pulsanti si trovano l'allineamento orizzontale nella finestra di dialogo.  
  
### Standard di controllo  
  
#### Generale  
  
-   Verificare che, quando possibile, esistono buone valori predefiniti per velocizzare l'interazione dell'utente e indirizzare gli utenti verso un risultato safe o comune.  
  
-   Verificare che i controlli standard funziona allo stesso modo, in modo che gli utenti sanno cosa accadrà in base all'esperienza precedente.  
  
#### Controllo Label  
  
-   Verificare che ogni controllo contiene un'etichetta e che ogni etichetta visivamente è associato il controllo \(in genere entro un intervallo di pixel 4\-6\) e che sia più vicino al controllo corrispondente rispetto ad altri controlli.  
  
-   Verificare che le etichette vengono posizionate allineamento a sinistra di un controllo a sinistra edge se posizionata di sopra e al centro orizzontalmente, in modo che la linea di base dell'etichetta è allineata alla linea di base del testo di input se posizionata a sinistra.  
  
-   Verificare che, se diverse etichette in pila e controlli di input sono posizionati a sinistra di un controllo, le etichette sono allineamento a sinistra e una distanza dal bordo della finestra di dialogo non scaricare mai destra e alla stessa distanza dai controlli. Coppie devono essere distribuite in modo uniforme a meno che non richiedono la spaziatura per indicare il raggruppamento.  
  
#### Controlli di input \(caselle di testo e caselle combinate\)  
  
-   Verificare che quando si utilizza il tipo di carattere ambiente predefinito, l'altezza di visualizzazione per le caselle di testo, caselle combinate e pulsanti sono tutti 23 pixel.  
  
-   Se viene utilizzato testo di suggerimento, verificare che il colore è impostato su `Environment.ControlEditHintText` tramite il servizio di colore.  
  
-   Se il campo è un campo obbligatorio che deve essere identificato come tali, verificare che:  
  
    -   che lo sfondo è impostato su `Environment.ControlEditRequiredBackground` e primo piano è impostato su `Environment.ControlEditRequiredHintText`  
  
    -   che vi sia testo di suggerimento all'interno del controllo che viene visualizzato come **"\< Required \>"**  
  
#### Controlli pulsante  
  
-   Verificare che i pulsanti sono una dimensione minima di 75 x 23 pixel, a meno che l'aggiunta di un testo più lungo.  
  
-   Verificare che i pulsanti destra e sinistra margini di 3\-5 pixel, nonché la spaziatura interna per il contenuto.  
  
-   È possibile utilizzare un piccolo pulsante quadrato con solo i puntini di sospensione **\[…\]** su di esso anziché di un **\[Sfoglia...\]** pulsante \(o simile\). Se utilizzato, verificare che il pulsante è 23 x 23 nella dimensione.  
  
-   Se è presente più di un **\[Sfoglia...\]** pulsante in una finestra di dialogo, quindi verificare che la versione abbreviata \(solo i puntini di sospensione **\[…\]**\) viene usato per tutti.  
  
-   Verificare che i puntini di sospensione **\[…\]** pulsanti non hanno un tasto di scelta rapida. Quando lo stato attivo sul controllo di input corrispondente, una scheda deve spostare lo stato attivo sul pulsante con puntini di sospensione.  
  
-   Verificare che i pulsanti, comandi e collegamenti di comando per avviare l'interfaccia utente secondaria per l'acquisizione di più input dell'utente devono terminare con i puntini di sospensione **\[…\]**.  
  
#### Collegamenti ipertestuali  
  
-   Verificare che un controllo hyperlink non lampeggia mai rosso quando sono attive. Si tratta di un indicatore che il servizio di colore non è in corso utilizzare  
  
-   Verificare che i colori di Visual Studio utilizzati sono:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Verificare che i collegamenti ipertestuali vengono visualizzati con alcun carattere di sottolineatura blu se incorporato in un paragrafo.  
  
#### Caselle di controllo  
  
-   Se una casella di controllo dispone di testo su più righe, verificare che la casella in linea con la prima riga del testo, non è centrato verticalmente tra tutte le righe.  
  
-   Verificare che le caselle di controllo sempre indicano una scelta binario e non mostrare all'utente o aprire nuove finestre o pagine.  
  
-   Se una casella di controllo presenta un'opzione correlata a un controllo di input, verificare che sia posizionato allineamento a sinistra e a stretto contatto con il controllo per indicare la relazione.  
  
-   Verificare che sia una casella di controllo **mai** utilizzata come mezzo per abilitare l'intero contenuto di una finestra di dialogo o pagina.  
  
#### Caselle di gruppo  
  
-   Verificare che una finestra di dialogo non contiene una casella di gruppo singola all'interno che contiene l'intero contenuto della finestra di dialogo.  
  
-   Verificare che siano presenti almeno due controlli all'interno di ogni casella di gruppo.  
  
-   Raramente deve essere presente più di due caselle di gruppo in una finestra di dialogo.  
  
-   Verificare che siano non disponibili alcuna casella di gruppo nidificato.  
  
### Icone  
  
-   Verificare che le icone siano visualizzati correttamente invertite quando il tema scuro.  
  
-   Verificare che tutte le icone sono basate su concetti di base.  
  
-   Verificare che ogni icona è distinct, facile da riconoscere e non contiene più di due concetti \(senza stato modificatore\/language\).  
  
-   Verificare che l'icona base centrato all'interno dello spazio.  
  
-   Verificare che tutte le icone vengono visualizzate leggibili in modalità contrasto elevato.  
  
-   Verificare che qualsiasi colore utilizzato in linea con gli standard di utilizzo di colore.  
  
-   Verificare che non siano senza aloni \(bordi\) per le icone. \(Se presente, alone deve corrispondere il colore di sfondo dell'interfaccia utente adiacente\).  
  
### Interfaccia utente abilitato per il tocco  
  
-   Verificare che siano sufficientemente grandi da essere facilmente touchable: minimo controlli interattivi **23 x 23 pixel** dimensioni  
  
-   Verificare che i controlli utilizzati più di frequente sono almeno **40 x 40 pixel** nella dimensione.  
  
-   Verificare che controlli interattivi almeno **5 pixel di spaziatura** tra di essi