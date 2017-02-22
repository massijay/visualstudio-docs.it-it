---
title: "Procedura: utilizzare frammenti XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: utilizzare frammenti XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile richiamare i frammenti XML utilizzando i due comandi seguenti dal menu di scelta rapida dell'editor XML.Il comando **Inserisci frammento** consente di inserire il frammento XML nella posizione del cursore.Il comando **Racchiudi tra** consente di inserire il frammento XML nel testo selezionato.Ogni frammento XML dispone di tipi di frammento designati.I tipi di frammento determinano se il frammento è disponibile con il comando **Inserisci frammento**, il comando **Racchiudi tra** o entrambi.  
  
 Dopo che il frammento XML è stato aggiunto all'editor, i campi modificabili nel frammento vengono evidenziati in giallo e il cursore viene posizionato nel primo campo modificabile.  
  
## Inserisci frammento  
 Nelle procedure riportate di seguito viene descritto come accedere al comando **Inserisci frammento**.  
  
> [!NOTE]
>  Il comando **Inserisci frammento** è disponibile anche tramite il tasto di scelta rapida \(CTRL\+K, quindi CTRL\+X\).  
  
#### Per inserire i frammenti dal menu di scelta rapida  
  
1.  Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.  
  
2.  Fare clic con il pulsante destro del mouse e scegliere **Inserisci frammento**.  
  
     Viene visualizzato un elenco dei frammenti XML disponibili.  
  
3.  Selezionare un frammento dall'elenco utilizzando il mouse, oppure digitare il nome del frammento e premere TAB o INVIO.  
  
#### Per inserire i frammenti dal menu IntelliSense  
  
1.  Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.  
  
2.  Scegliere **IntelliSense** dal menu **Modifica**, quindi scegliere **Inserisci frammento**.  
  
     Viene visualizzato un elenco dei frammenti XML disponibili.  
  
3.  Selezionare un frammento dall'elenco utilizzando il mouse, oppure digitare il nome del frammento e premere TAB o INVIO.  
  
#### Per inserire i frammenti dall'elenco Completa parola di IntelliSense  
  
1.  Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.  
  
2.  Iniziare a digitare il frammento XML che si desidera aggiungere al file.Se il completamento automatico è attivato, viene visualizzato l'elenco Completa parola di IntelliSense.Se l'elenco non viene visualizzato, premere CTRL\+BARRA SPAZIATRICE per attivarlo.  
  
3.  Selezionare il frammento XML dall'elenco Completa parola.  
  
4.  Premere TAB, TAB per richiamare il frammento XML.  
  
> [!NOTE]
>  In alcuni casi è possibile che il frammento XML non venga richiamato.Ad esempio, se si tenta di inserire un elemento `xs:complexType` all'interno di un nodo `xs:element`, l'editor non genera alcun frammento XML.Quando un elemento `xs:complexType` viene utilizzato all'interno di un nodo `xs:element`, non vengono rilevati attributi o sottoelementi obbligatori, pertanto l'editor non disporrà di alcun dato da inserire.  
  
#### Per inserire i frammenti dal nome del collegamento  
  
1.  Posizionare il cursore nel punto in cui si desidera inserire il frammento XML.  
  
2.  Digitare `<` nel riquadro dell'editor.  
  
3.  Premere ESC per chiudere l'elenco Completa parola di IntelliSense.  
  
4.  Digitare il nome collegamento del frammento, quindi premere TAB per richiamare il frammento XML.  
  
## Racchiudi tra  
 Nelle procedure riportate di seguito viene descritto come accedere al comando **Racchiudi tra**.  
  
> [!NOTE]
>  Il comando **Racchiudi tra** è disponibile anche tramite il tasto di scelta rapida \(CTRL\+K, quindi CTRL\+S\).  
  
#### Per utilizzare il comando dal menu di scelta rapida  
  
1.  Selezionare il testo da racchiudere nell'editor XML.  
  
2.  Fare clic con il pulsante destro del mouse e scegliere **Racchiudi tra**.  
  
     Verrà visualizzato un elenco delle scelte disponibili con i frammenti XML.  
  
3.  Selezionare un frammento dall'elenco utilizzando il mouse, oppure digitare il nome del frammento e premere TAB o INVIO.  
  
#### Per utilizzare il comando dal menu IntelliSense  
  
1.  Selezionare il testo da racchiudere nell'editor XML.  
  
2.  Scegliere **IntelliSense** dal menu **Modifica**, quindi scegliere **Racchiudi tra**.  
  
     Viene visualizzato un elenco delle scelte disponibili con i frammenti XML.  
  
3.  Selezionare un frammento dall'elenco utilizzando il mouse, oppure digitare il nome del frammento e premere TAB o INVIO.  
  
## Utilizzo dei frammenti XML  
 Una volta scelto il frammento XML, il testo del frammento di codice viene inserito automaticamente nella posizione del cursore.I campi modificabili del frammento vengono evidenziati e il primo campo modificabile viene selezionato automaticamente.Il campo attualmente selezionato è di tipo boxed.  
  
 Quando si seleziona un campo, è possibile digitare un nuovo valore per tale campo.Premendo TAB è possibile scorrere i campi modificabili del frammento. Premendo MAIUSC\+TAB è possibile scorrerli in ordine inverso.Se si fa clic su un campo il cursore viene posizionato all'interno del campo, se si fa doppio clic il campo viene selezionato.Quando un campo è evidenziato, potrebbe essere visualizzata la finestra con la descrizione del campo.  
  
 È modificabile solo la prima istanza di un determinato campo.Quando il campo è evidenziato, le altre istanze del campo sono tratteggiate.Quando si modifica il valore di un campo modificabile, il campo viene modificato ovunque venga utilizzato nel frammento.  
  
 Premere INVIO o ESC per annullare la modifica del campo e tornare alla visualizzazione normale dell'editor.  
  
 È possibile cambiare i colori predefiniti dei campi modificabili del frammento di codice modificando l'impostazione del campo nel riquadro **Tipi di carattere e colori** della finestra di dialogo **Opzioni**.Per ulteriori informazioni, vedere [Procedura: modificare i tipi di carattere e i colori utilizzati nell'editor](../Topic/How%20to:%20Change%20Fonts%20and%20Colors%20in%20the%20Editor.md).  
  
## Vedere anche  
 [Frammenti di codice XML](../xml-tools/xml-snippets.md)   
 [Procedura: generare un frammento XML da XML Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)   
 [Procedura: creare frammenti XML](../xml-tools/how-to-create-xml-snippets.md)