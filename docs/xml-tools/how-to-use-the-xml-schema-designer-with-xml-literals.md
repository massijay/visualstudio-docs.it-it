---
title: "Procedura: utilizzare Progettazione XML Schema con i valori letterali XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: utilizzare Progettazione XML Schema con i valori letterali XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene descritto come visualizzare uno schema associato a un valore letterale XML in un progetto di Visual Basic..  
  
### Per creare un nuovo progetto di applicazione console di Visual Basic  
  
1.  Avviare Visual Studio 2010.  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi **Progetto**.Verrà visualizzata la finestra di dialogo **Nuovo progetto**.Per **Tipi progetto**, selezionare **Altri linguaggi** quindi **Visual Basic**.Per **Modelli**, selezionare Applicazione console.Quindi digitare `XMLLiterals` nel campo **Nome** e un percorso del progetto nel campo **Percorso**.Fare clic su **OK**.  
  
     Il nuovo progetto è creato.Il progetto XMLLiterals contiene un file di origine di Visual Basic, Module1.vb.  
  
### Per aggiungere un file XSD esistente al progetto  
  
1.  Aprire un nuovo file di testo in Blocco note.Copiare il codice di esempio di XML Schema da [Schema di ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md) e incollarlo sul file.  
  
2.  Salvare il file in un percorso con il nome PurchaseOrderSchema.xsd.  
  
3.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul nome del progetto, selezionare **Aggiungi**, quindi fare clic su **Elemento esistente...**.Verrà visualizzata la finestra di dialogo **Aggiungi elemento esistente**.Individuare il file PurchaseOrderSchema.xsd, selezionarlo e fare clic su **Aggiungi**.  
  
     Il progetto XMLLiterals contiene ora due file: Module1.vb e PurchaseOrderSchema.xsd.  
  
### Per aggiungere codice Visual Basic con un valore letterale XML, in base al file XSD incluso nel progetto  
  
1.  Sostituire il codice nel file Module1.vb con il codice seguente:  
  
    ```  
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
    Module Module1  
        Sub Main()  
  
            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                 <ns:ShipTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:ShipTo>  
                                 <ns:BillTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:BillTo>  
                             </ns:PurchaseOrder>  
  
        End Sub  
    End Module  
    ```  
  
2.  Fare clic con il pulsante destro del mouse su un qualsiasi nodo XML in un'importazione di valore letterale XML o spazio dei nomi XML e selezionare il comando **Mostra in Schema Explorer**.  
  
     XML Schema Explorer viene visualizzato accanto a un file di Visual Basic che dispone di un valore letterale XML associato al set di schemi XML.