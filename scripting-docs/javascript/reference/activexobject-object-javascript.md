---
title: "Oggetto ActiveXObject (JavaScript) | Microsoft Docs"
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
  - "ActiveXObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ActiveXObject (oggetto)"
  - "oggetti di automazione, ActiveXObject (oggetti)"
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Oggetto ActiveXObject (JavaScript)
Attiva e restituisce un riferimento a un oggetto di automazione.  
  
 Questo oggetto viene utilizzato per istanziare gli oggetti di automazione e non dispone di membri.  
  
> [!WARNING]
>  Questo oggetto è un'estensione Microsoft ed è supportato in Internet Explorer, non solo nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Sintassi  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## Parametri  
 `newObj`  
 Obbligatorio.  Nome della variabile a cui l'oggetto `ActiveXObject` è assegnato.  
  
 `servername`  
 Obbligatorio.  Nome dell'applicazione che fornisce l'oggetto.  
  
 `typename`  
 Obbligatorio.  Tipo o classe dell'oggetto da creare.  
  
 `location`  
 Facoltativa.  Nome del server di rete in cui verrà creato l'oggetto.  
  
## Note  
 I server di automazione forniscono almeno un tipo di oggetto.  Un programma di elaborazione di testi, ad esempio, può fornire un oggetto applicazione, un oggetto documento e un oggetto barra degli strumenti.  
  
 È possibile identificare i valori `servername.typename` su un computer host nella chiave del Registro di sistema `HKEY_CLASSES_ROOT`.  Di seguito sono riportati alcuni esempi di valori disponibili a seconda dei programmi installati:  
  
-   Excel.Application  
  
-   Excel.Chart  
  
-   Scripting.FileSystemObject  
  
-   WScript.Shell  
  
-   Word.Document  
  
> [!IMPORTANT]
>  Gli oggetti ActiveX possono presentare problemi di sicurezza.  Per utilizzare `ActiveXObject`, potrebbe essere necessario modificare le impostazioni di sicurezza in Internet Explorer per l'area di sicurezza rilevante.  Ad esempio, per l'area Intranet locale, generalmente è necessario modificare un'impostazione personalizzata su "Inizializza ed esegui script controlli ActiveX non contrassegnati come sicuri per lo script".  
  
 Per identificare i membri di un oggetto di automazione che è possibile utilizzare nel codice, potrebbe essere necessario utilizzare un visualizzatore oggetti COM, ad esempio il [visualizzatore di oggetti OLE\/COM](http://msdn.microsoft.com/library/d0kh9f4c.aspx), se nessuna documentazione di riferimento è disponibile per l'oggetto di automazione.  
  
 Per creare un oggetto di automazione, assegnare il nuovo oggetto `ActiveXObject` a una variabile oggetto:  
  
```javascript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 Questo codice avvia l'applicazione creando l'oggetto \(in questo caso, un foglio di lavoro di Microsoft Excel\).  Una volta che l'oggetto è stato creato, è possibile fare riferimento a quest'ultimo nel codice utilizzando la variabile oggetto definita.  Nell'esempio di codice seguente è possibile accedere alle proprietà e ai metodi del nuovo oggetto tramite la variabile oggetto `ExcelSheet` e tramite gli altri oggetti Excel, tra cui l'oggetto Application e la raccolta ActiveSheet.Cells.  
  
```javascript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9, standard di Internet Explorer 10, standard di Internet Explorer 11.  Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
> [!NOTE]
>  La creazione di `ActiveXObject` su un server remoto non è supportata nella [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] o nelle versioni successive.  
  
## Vedere anche  
 [Funzione GetObject](../../javascript/reference/getobject-function-javascript.md)   
 [Applicazione di esempio per autenticazione univoca tramite funzionalità chiave di HTML5\/WCF](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)