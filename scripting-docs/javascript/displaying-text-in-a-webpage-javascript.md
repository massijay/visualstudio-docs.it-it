---
title: "Visualizzazione di testo in una pagina Web (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, scrivere"
  - "JavaScript, scrittura di testo"
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Visualizzazione di testo in una pagina Web (JavaScript)
Esistono diversi modi per visualizzare testo in una pagina Web.  Ognuno presenta vantaggi e svantaggi e supporta usi specifici.  
  
## Visualizzazione di testo  
  
-   La modalità consigliata per visualizzare testo è quella di creare un elemento e di scrivere nella proprietà [textContent](http://msdn.microsoft.com/it-it/e530667f-f8fa-4b6d-a47c-4d5c75e71265):  
  
    ```javascript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     In questo esempio, il valore di `text` è "my text".  Tuttavia, il valore derivante dal recupero o dall'impostazione della proprietà [textContent](http://msdn.microsoft.com/it-it/e530667f-f8fa-4b6d-a47c-4d5c75e71265) su un nodo padre potrebbe includere il contenuto di testo dei figli del nodo.  L'esempio seguente mostra che [textContent](http://msdn.microsoft.com/it-it/e530667f-f8fa-4b6d-a47c-4d5c75e71265) impostato su un nodo figlio viene incluso nel valore di [textContent](http://msdn.microsoft.com/it-it/e530667f-f8fa-4b6d-a47c-4d5c75e71265) del nodo padre:  
  
    ```javascript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     In questo esempio, il valore di `text` è "\[nested\]".  
  
-   È anche possibile creare un elemento e scrivere nelle relative proprietà [innerHTML](http://msdn.microsoft.com/it-it/library/ms533897\(v=vs.85\).aspx) o [innerText](http://msdn.microsoft.com/it-it/library/ms533899\(v=vs.85\).aspx).  L'impostazione di queste proprietà influisce solo sul testo nell'elemento stesso, non nei relativi elementi figlio.  Tuttavia, queste proprietà presentano anche alcuni svantaggi:  
  
    -   La proprietà [innerText](http://msdn.microsoft.com/it-it/library/ms533899\(v=vs.85\).aspx) non funziona in tutti i browser, quindi è consigliabile evitarla per motivi di compatibilità.  
  
    -   La proprietà [innerText](http://msdn.microsoft.com/it-it/library/ms533899\(v=vs.85\).aspx) è influenzata dagli stili CSS e non viene visualizzata se l'elemento è nascosto.  
  
    -   La proprietà [innerHTML](http://msdn.microsoft.com/it-it/library/ms533897\(v=vs.85\).aspx) ottiene e imposta sia testo che nodi annidati.  Se non è protetta, potrebbe essere usata per attacchi script injection.  Inoltre, l'impostazione su testo senza tag HTML rimuove tutti i nodi precedentemente impostati.  
  
-   È possibile usare il metodo `document.write` senza dover creare un elemento.  Tuttavia, l'uso di questo metodo fa sì che l'intera pagina Web venga cancellata, che potrebbe non corrispondere al risultato desiderato.  
  
     L'esempio seguente illustra uno degli svantaggi dell'uso di `document.write`.  Lo script è progettato per visualizzare l'ora ogni 5 secondi, ma la mostra solo due volte.  Prima che venga chiamato `document.write` per la seconda volta, il caricamento della pagina sarà stato completato e `document.write` quindi rimuove l'intera pagina \(chiama `document.open`\).  A questo punto, la funzione `ShowTime` non esiste più.  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     Per correggere il codice precedente, rimuovere la riga di codice che contiene `document.write` e rimuovere il commento dalle due righe di codice seguenti impostate come commento.  
  
-   È anche possibile usare `alert`, `prompt` o la funzione `confirm` che visualizza un messaggio in una finestra popup.  Nella maggior parte dei casi non è consigliabile usare una finestra popup in un Web browser.  La maggior parte dei browser moderni ha impostazioni che bloccano automaticamente le finestre popup, perciò il messaggio potrebbe non essere visualizzato.  Inoltre, quando si usano le finestre popup, è possibile entrare in un ciclo infinito che rende impossibile per l'utente chiudere la pagina Web nel modo abituale.