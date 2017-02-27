---
title: "Procedura dettagliata: eseguire il debug di un foglio di stile XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura dettagliata: eseguire il debug di un foglio di stile XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nei passaggi della procedura dettagliata viene illustrato come utilizzare il debugger XSLT.I passaggi comprendono la visualizzazione delle variabili, l'impostazione dei punti di interruzione e l'esecuzione del codice un'istruzione alla volta.Nel foglio di stile vengono elencati tutti i libri con prezzo inferiore a quello del libro medio.  
  
### Operazioni preliminari per la procedura dettagliata  
  
1.  Chiudere eventuali soluzioni aperte.  
  
2.  Copiare i due file di esempio nel computer locale.  
  
## Avvio del debug  
  
#### Per avviare il debug  
  
1.  Dal menu **File** scegliere **Apri**, quindi **File**.  
  
2.  Individuare il file belowAvg.xsl e fare clic su **Apri**.  
  
     Il foglio di stile viene aperto nell'editor XML.  
  
3.  Fare clic sul pulsante Sfoglia \(**...**\) nel campo di **Input** della finestra Proprietà del documento.  
  
4.  Individuare il file books.xml e fare clic su **Apri**.  
  
     In questo modo viene impostato il file del documento di origine utilizzato per la trasformazione XSLT.  
  
5.  Fare clic con il pulsante destro del mouse sul tag di inizio `xsl:if`, scegliere **Punto di interruzione**, quindi fare clic su **Inserisci punto di interruzione**.  
  
6.  Fare clic sul pulsante **Debug XSLT** sulla barra degli strumenti dell'editor XML.  
  
 Verrà avviato il processo di debug e verranno aperte diverse nuove finestre utilizzate dal debugger.  
  
 In due finestre vengono visualizzati il documento di input e il foglio di stile.Il debugger utilizza queste finestre per mostrare lo stato di esecuzione correnteed è posizionato sull'elemento `xsl:if` del foglio di stile e sul primo nodo libro nel file books.xml.  
  
 Nella finestra Variabili locali vengono visualizzate tutte le variabili locali e i relativi valori correnti,incluse le variabili definite nel foglio di stile e quelle utilizzate dal debugger per tenere traccia dei nodi presenti nel contesto.  
  
 Nella finestra **Output XSL** viene visualizzato l'output della trasformazione XSL.Questa finestra è separata dalla finestra **Output di Visual Studio**.  
  
## Finestra Espressioni di controllo  
  
#### Per utilizzare la finestra Espressioni di controllo  
  
1.  Dal menu **Debug** scegliere **Windows**, **Espressioni di controllo**, quindi fare clic su **Espressione di controllo 1**.  
  
     In questo modo viene visualizzata la finestra Espressione di controllo 1.  
  
2.  Digitare `$bookAverage` nel campo **Nome** e premere INVIO.  
  
     Il valore della variabile `$bookAverage` viene visualizzato nella finestra.  
  
3.  Digitare `self::node()` nel campo **Nome** e premere INVIO.  
  
     `self::node()` è un'espressione XPath che restituisce il nodo di contesto corrente.Il valore dell'espressione XPath `self::node()` costituisce il primo nodo libro. Il valore verrà modificato durante le fasi della trasformazione.  
  
4.  Espandere il nodo `self::node()`, quindi il nodo `price`.  
  
     Ciò consente di visualizzare il valore del prezzo del libro e di confrontarlo facilmente con il valore `$bookAverage`.Poiché il prezzo del libro è maggiore del prezzo medio, la condizione `xsl:if` dovrebbe essere eseguita correttamente.  
  
## Esecuzione del codice un'istruzione alla volta  
 Il debugger consente di eseguire il codice una riga alla volta.  
  
#### Per eseguire il codice un'istruzione alla volta  
  
1.  Premere **F5** per continuare.  
  
     Poiché il nodo del primo libro ha soddisfatto la condizione `xsl:if`, il nodo libro viene aggiunto alla finestra di output XSL.Il debugger continua l'esecuzione se non viene posizionato di nuovo sull'elemento `xsl:if` nel foglio di stile.Il debugger è ora posizionato sul secondo nodo libro nel file books.xml.  
  
     Nella finestra Watch1 il valore `self::node()` viene modificato nel secondo nodo libro.Analizzando il valore dell'elemento prezzo, è possibile determinare che il prezzo è maggiore del prezzo medio e che pertanto la condizione `xsl:if` non dovrebbe essere eseguita correttamente.  
  
2.  Premere **F5** per continuare.  
  
     Poiché il secondo nodo libro non soddisfa la condizione `xsl:if`, il nodo libro non viene aggiunto alla finestra di output XSL.Il debugger continua l'esecuzione se non viene posizionato di nuovo sull'elemento `xsl:if` nel foglio di stile.Il debugger è ora posizionato sul terzo nodo `book` nel file books.xml.  
  
     Nella finestra Watch1 il valore `self::node()` viene modificato nel terzo nodo libro.Analizzando il valore dell'elemento `price`, è possibile determinare che il prezzo è inferiore al prezzo medio e che pertanto la condizione `xsl:if` dovrebbe essere eseguita correttamente.  
  
3.  Premere **F5** per continuare.  
  
     Poiché la condizione `xsl:if` è stata soddisfatta, il terzo libro viene aggiunto alla finestra di output XSL.Tutti i libri nel documento XML sono stati elaborati e il debugger si arresta.  
  
## File di esempio  
 I due file seguenti vengono utilizzati nella procedura dettagliata.  
  
### belowAvg.xsl  
  
```  
<?xml version='1.0'?>  
<xsl:stylesheet version="1.0"  
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:output method="xml" encoding="utf-8"/>  
  <xsl:template match="/">  
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>  
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>  
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>  
    <books>  
      <!--Books That Cost Below Average-->  
      <xsl:for-each select="/bookstore/book">  
        <xsl:if test="price < $bookAverage">  
          <xsl:copy-of select="."/>  
        </xsl:if>  
      </xsl:for-each>  
    </books>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### books.xml  
  
```  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database -->  
<bookstore>  
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">  
    <title>The Autobiography of Benjamin Franklin</title>  
    <author>  
      <first-name>Benjamin</first-name>  
      <last-name>Franklin</last-name>  
    </author>  
    <price>8.99</price>  
  </book>  
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">  
    <title>The Confidence Man</title>  
    <author>  
      <first-name>Herman</first-name>  
      <last-name>Melville</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">  
    <title>The Gorgias</title>  
    <author>  
      <name>Plato</name>  
    </author>  
    <price>9.99</price>  
  </book>  
</bookstore>  
```  
  
## Vedere anche  
 [Debug di XSLT](../xml-tools/debugging-xslt.md)