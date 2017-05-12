---
title: "Oggetto VBArray (JavaScript) | Microsoft Docs"
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
  - "VBArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "costante dell'oggetto VBArray"
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Oggetto VBArray (JavaScript)
Fornisce l'accesso alle matrici protette di Visual Basic.  
  
> [!WARNING]
>  Questo oggetto è supportato solo in Internet Explorer e non nelle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Sintassi  
  
```  
  
varName = new VBArray(safeArray)  
```  
  
## Parametri  
 `varName`  
 Obbligatorio. Nome della variabile a cui l'oggetto VBArray è assegnato.  
  
 *safeArray*  
 Obbligatorio. Un valore VBArray.  
  
## Note  
 Gli oggetti VBArray sono di sola lettura e non possono essere creati direttamente. L'argomento *safeArray* deve disporre di un valore VBArray prima di essere passato al costruttore VBArray. Ciò può essere ottenuto solo recuperando il valore da un oggetto ActiveX o altro esistente.  
  
 Gli oggetti VBArray possono avere più dimensioni. Gli indici di ogni dimensione possono essere diversi. Il metodo **dimensions** recupera il numero di dimensioni della matrice; i metodi `lbound` e `ubound` recuperano l'intervallo di indici usato da ogni dimensione.  
  
## Esempio  
 L'esempio seguente si compone di tre parti: La prima parte è il codice VBScript per creare una matrice protetta di Visual Basic. La seconda parte è il codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che converte la matrice protetta di Visual Basic in una matrice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Entrambe queste parti vanno inserite nella sezione \<HEAD\> di una pagina HTML. La terza parte è il codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che va inserito nella sezione \<BODY\> per eseguire le altre due parti.  
  
```javascript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(j, i) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## Proprietà  
 L'oggetto `VBArray` non ha alcuna proprietà.  
  
## Metodi  
 [Metodo dimensions](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [Metodo getItem](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [Metodo lbound](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [Metodo toArray](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [Metodo ubound](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
## Vedere anche  
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)