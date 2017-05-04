---
title: "Funzione GetObject (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GetObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetObject (funzione)"
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Funzione GetObject (JavaScript)
Restituisce un riferimento a un oggetto di automazione da un file.  
  
> [!NOTE]
>  Questa funzione non è supportata in Internet Explorer 9 \(modalità standard\) o versioni successive.  
  
## Sintassi  
  
```  
GetObject([pathname] [, class])  
```  
  
## Parametri  
 `pathname`  
 Opzionale.  Percorso completo e nome del file contenente l'oggetto da recuperare.  Se `pathname` viene omesso, è necessario `class`.  
  
 `class`  
 Opzionale.  Classe dell'oggetto.  
  
 L'argomento `class` utilizza la sintassi `appname.objectype` e presenta le seguenti parti:  
  
 `appname`  
 Necessario.  Nome dell'applicazione che fornisce l'oggetto.  
  
 `objectype`  
 Necessario.  Tipo o classe dell'oggetto da creare.  
  
## Note  
 La funzione `GetObject` non è supportata nella [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] o versioni successive.  
  
 Utilizzare la funzione `GetObject` per accedere a un oggetto di automazione da un file.  Assegnare l'oggetto restituito da `GetObject` alla variabile oggetto.  Ad esempio:  
  
```javascript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Quando si esegue questo codice, viene avviata l'applicazione associata al percorso specificato in `pathname` e viene attivato l'oggetto incluso nel file specificato.  Se `pathname` è una stringa di lunghezza zero \(""\), `GetObject` restituisce una nuova istanza dell'oggetto con il tipo di classe specificato.  Se l'argomento `pathname` viene omesso, `GetObject` restituirà un oggetto correntemente attivo del tipo specificato.  Se non esiste alcun oggetto del tipo specificato, verrà generato un errore.  
  
 In alcune applicazioni è possibile attivare parte di un file.  Per eseguire questa operazione, è necessario aggiungere un punto esclamativo \(\!\) alla fine del nome del file, seguito da una stringa che identifica la parte del file che si desidera attivare.  Per informazioni sulla creazione della stringa, vedere la documentazione dell'applicazione che ha creato l'oggetto.  
  
 In un'applicazione di disegno, ad esempio, è possibile che esistano più livelli per un disegno archiviato in un file.  Per attivare il livello layer3 del documento `SCHEMA.CAD`, è possibile utilizzare il codice seguente:  
  
```javascript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Se non si specifica la classe dell'oggetto, tramite l'automazione vengono identificati l'applicazione da avviare e l'oggetto da attivare in base al nome del file specificato.  Con alcuni file, tuttavia, vengono supportate più classi di oggetti.  Un disegno, ad esempio, può supportare tre diversi tipi di oggetti, ovvero un oggetto applicazione, un oggetto disegno e un oggetto barra degli strumenti, appartenenti tutti allo stesso file.  Per specificare l'oggetto di un file da attivare, utilizzare l'argomento facoltativo `class`.  Ad esempio:  
  
```javascript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 Nell'esempio, `FIGMENT` è il nome di un'applicazione di disegno e `DRAWING` è uno dei tipi di oggetto supportati.  Una volta attivato un oggetto, è possibile farvi riferimento nel codice utilizzando la variabile oggetto definita.  Nell'esempio precedente, per accedere alle proprietà e ai metodi del nuovo oggetto, viene utilizzata la variabile oggetto `MyObject`.  Ad esempio:  
  
```javascript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Utilizzare la funzione `GetObject` quando è disponibile un'istanza corrente dell'oggetto o se si desidera creare l'oggetto con un file già caricato.  In caso contrario, utilizzare l'oggetto `ActiveXObject`.  
  
 Se un oggetto viene registrato come oggetto a singola istanza, verrà creata una sola istanza dell'oggetto, indipendentemente dal numero di esecuzioni dell'oggetto `ActiveXObject`.  Con un oggetto a singola istanza, `GetObject` restituisce sempre la stessa istanza se viene chiamata utilizzando una sintassi con stringa di lunghezza zero \(""\) e viene generato un errore se l'argomento `pathname` viene omesso.  
  
## Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7 e standard di Internet Explorer 8.  Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
## Vedere anche  
 [Oggetto ActiveXObject](../../javascript/reference/activexobject-object-javascript.md)