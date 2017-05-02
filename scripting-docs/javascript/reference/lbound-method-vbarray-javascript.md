---
title: "Metodo lbound (VBArray) (JavaScript) | Microsoft Docs"
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
  - "lbound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lbound (metodo)"
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Metodo lbound (VBArray) (JavaScript)
Restituisce il valore di indice minimo utilizzato nella dimensione specificata di un oggetto VBArray.  
  
## Sintassi  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## Parametri  
 *safeArray*  
 Necessario.  Un oggetto VBArray  
  
 `dimension`  
 Opzionale.  Dimensione dell'oggetto VBArray di cui si desidera individuare l'indice del limite inferiore.  Se omesso, il metodo `lbound` funziona esattamente come se fosse stato passato il valore 1.  
  
## Note  
 Se l'oggetto VBArray è vuoto, mediante il metodo `lbound` viene restituito undefined.  Se `dimension` è negativo o maggiore del numero di dimensioni dell'oggetto VBArray, verrà generato un errore di indice non compreso nell'intervallo.  
  
## Esempio  
 L'esempio seguente è composto da tre parti.  La prima parte corrisponde al codice VBScript per la creazione di un Array di tipo Safe di Visual Basic.  La seconda corrisponde al codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] per la determinazione del numero di dimensioni dell'Array di tipo Safe e del limite inferiore di ciascuna dimensione.  Dato che l'Array di tipo Safe viene creato in VBScript e non in Visual Basic, il limite inferiore sarà sempre uguale a zero.  Entrambe queste parti sono incluse nella sezione \<HEAD\> di una pagina HTML.  La terza parte corrisponde al codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] incluso nella sezione \<BODY\> per l'esecuzione delle prime due parti.  
  
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
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10.  Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Vedere la pagina relativa alle [informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
 **Si applica a**: [Oggetto VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## Vedere anche  
 [Metodo dimensions \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Metodo getItem \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Metodo toArray \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Metodo ubound \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)