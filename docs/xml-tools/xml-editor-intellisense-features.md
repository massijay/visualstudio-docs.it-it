---
title: "Funzionalit&#224; IntelliSense dell&#39;editor XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzionalit&#224; IntelliSense dell&#39;editor XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML fornisce funzionalità IntelliSense avanzate paragonabili a quelle di altri editor di linguaggio forniti in Visual Studio.In questa sezione viene illustrato come utilizzare IntelliSense con documenti XML Schema Definition Language \(XSD\) e XSLT.  
  
## IntelliSense in un documento XSD  
 Dopo che uno schema è stato associato al documento, viene visualizzato un elenco a discesa degli elementi previsti ogni volta che si digita `"<"` o si seleziona il pulsante **Visualizza l'elenco membri di un oggetto** sulla barra degli strumenti dell'editor XML.Per informazioni sull'associazione degli schemi ai documenti XML, vedere [Convalida di documenti XML](../xml-tools/xml-document-validation.md).  
  
 Quando si preme BARRA SPAZIATRICE all'interno di un tag di inizio, viene visualizzato anche un elenco a discesa contenente tutti gli attributi che possono essere aggiunti all'elemento corrente.  
  
 Quando si digita `"="` per il valore di un attributo oppure la virgoletta di apertura per il valore, viene visualizzato anche un elenco dei possibili valori dell'attributo.I valori vengono forniti solo se lo schema fornisce valori enumerati mediante i facet `xsd:enumeration` o se l'attributo è di tipo `Boolean`.In IntelliSense Viene inoltre fornito un elenco dei codici lingua noti per `xml:lang` o per qualsiasi `simpleType` derivato da `xsd:language`.Per le dichiarazioni dello spazio dei nomi, viene fornito un elenco di IntelliSense dei valori `targetNamespace` noti.  
  
 Un elenco di IntelliSense dei valori possibili viene inoltre visualizzato quando si digita `">"` per chiudere un tag di inizio se l'elemento è un `simpleType`.Il comportamento degli elementi è simile al comportamento degli attributi descritto nel paragrafo precedente.  
  
 Negli elenchi di IntelliSense vengono visualizzate anche le descrizioni comandi basate sulle informazioni relative a `xsd:annotation` e `xsd:documentation` rilevate nello schema associato.  
  
## IntelliSense in un documento XSLT  
 Dopo avere aggiunto un modello denominato o un attributo al documento XSLT, è possibile utilizzare IntelliSense per inserire gli elementi seguenti:  
  
-   Nomi del set di attributi.  
  
-   Modalità modello.  
  
-   Nomi di modello.  
  
-   Nomi del parametro per una determinata modalità.  
  
-   Nomi del parametro per un determinato modello denominato.  
  
 Per ulteriori informazioni, vedere l'argomento [Procedura dettagliata: utilizzo di XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md).  
  
## Completamento automatico  
 L'editor XML, inoltre, semplifica la procedura di modifica del codice XML in quanto la sintassi XML richiesta viene inserita automaticamente.Ad esempio, se si digita il seguente tag di inizio:  
  
 `<book>`  
  
 L'editor XML inserisce il tag di fine e posiziona il cursore dopo il tag di inizio.Di seguito è riportato un esempio di questa funzione \(il carattere "&#124;" indica la posizione del cursore\):  
  
 `<book>`&#124;`</book>`  
  
 Dal momento che i valori degli attributi devono essere sempre racchiusi tra virgolette, queste vengono inserite automaticamente dall'editor XML.Se ad esempio si digita quanto segue:  
  
 `<book title=`  
  
 L'editor XML aggiunge le virgolette e posiziona il cursore tra le virgolette:  
  
 `<book title="`&#124;`"`  
  
 Analogamente, l'editor XML inserisce automaticamente anche la seguente sintassi XML:  
  
-   Termina un'istruzione di elaborazione: `?>`  
  
-   Termina un blocco CDATA: `]]>`  
  
-   Termina un commento: `-->`  
  
-   Termina una dichiarazione DTD: `>`  
  
 L'editor XML, inoltre, è in grado di inserire automaticamente una dichiarazione dello spazio dei nomi se si seleziona un elemento o attributo completo dello spazio dei nomi proveniente da un elenco di IntelliSense e lo spazio dei nomi per quell'elemento o attributo non è ancora nell'ambito.  
  
 Ad esempio, se dall'elenco di IntelliSense si seleziona l'elemento `e:Book` in cui il prefisso è associato allo spazio dei nomi `http://books` che non è stato dichiarato nel documento, l'editor XML inserirà automaticamente la dichiarazione dello spazio dei nomi richiesta.Di seguito è riportato il testo XML risultante:  
  
 `<e:Book xmlns:e="http://books"`  
  
## Corrispondenza parentesi graffe  
 Nell'editor XML è inclusa una funzionalità per l'evidenziazione delle parentesi graffe, che fornisce un feedback immediato sugli elementi appena chiusi.È inoltre possibile utilizzare il tasto di scelta rapida \(CTRL\+\]\) per passare da una parentesi graffa a quella corrispondente.  
  
 L'editor XML effettua tale operazione per i seguenti elementi:  
  
-   Tag di inizio e di fine corrispondenti.  
  
-   Qualsiasi coppia di parentesi angolari "\<" o "\>".  
  
-   Inizio e fine dei commenti.  
  
-   Inizio e fine delle istruzioni di elaborazione.  
  
-   Inizio e fine dei blocchi CDATA.  
  
-   Inizio e fine delle dichiarazioni DTD.  
  
-   Virgolette di apertura e chiusura sugli attributi.  
  
## Modifica delle opzioni IntelliSense  
 Le funzionalità IntelliSense e di completamento automatico sono abilitate per impostazione predefinita.Tuttavia, è possibile modificare le impostazioni relative alle opzioni degli strumenti.  
  
 Nella sezione **Inserimento automatico** della pagina **Varie** viene controllato il seguente comportamento:  
  
|Nome|Descrizione|  
|----------|-----------------|  
|Tag di chiusura|Inserisce i tag di chiusura per i nuovi elementi.|  
|Virgolette per attributi|Inserisce i valori di attributo tra virgolette quando si immette un nuovo nome di attributo.|  
|Altro markup|Completa commenti, CDATA, DOCTYPE, istruzioni di elaborazione e altre dichiarazioni dei markup.|  
  
#### Per modificare il comportamento del completamento automatico  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Espandere **Editor di testo**, quindi espandere **XML** e scegliere **Varie**.  
  
3.  Apportare le eventuali modifiche alla sezione **Inserimento automatico** e fare clic su **OK**.  
  
## Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)   
 [Utilizzo di IntelliSense](../ide/using-intellisense.md)   
 [Procedura dettagliata: utilizzo di XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)