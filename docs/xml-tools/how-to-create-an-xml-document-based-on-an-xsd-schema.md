---
title: "Procedura: creare un documento XML in base allo schema XSD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura: creare un documento XML in base allo schema XSD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La funzionalità **Genera XML di esempio** genera un file XML di esempio basato sul file XML Schema \(XSD\).  
  
 È possibile utilizzare questa opzione per gli scenari seguenti:  
  
-   Per comprendere l'utilizzo di diversi costrutti nello schema.  
  
-   Per confermare che lo schema funziona come previsto.  
  
 La funzionalità **Genera XML di esempio** è disponibile solo in caso di elementi globali e richiede un set di schemi XML valido.  
  
 Questa funzionalità genera di norma documenti XML validi.Tuttavia, se lo schema contiene uno o più degli elementi seguenti, l'esempio potrebbe non essere valido:  
  
-   I vincoli di identità `xs:key`, `xs:keyref` e `xs:unique`.  
  
-   Facet `xs:pattern`.  
  
-   Enumerazioni di tipo `xs:QName`.  
  
-   I tipi `xs:ENTITY`, `xs:ENTITIES` e `xs:NOTATION`.  
  
 Si noti inoltre che il contenuto `xs:base64Binary` sarà generato solo se le enumerazioni si verificano nello schema per il tipo specificato.  
  
### Per generare un documento di istanza XML basato sul file XSD  
  
1.  Seguire la procedura indicata in [Procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  In [XML Schema Explorer](../xml-tools/xml-schema-explorer.md), fare clic con il pulsante destro del mouse sull'elemento globale `PurchaseOrder`.Selezionare **Genera XML di esempio**.  
  
     Quando si seleziona questa opzione, il file PurchaseOrder.xml con il seguente contenuto XML di esempio sarà generato e aperto nell'editor XML:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">  
      <ShipTo country="US">  
        <name>name1</name>  
        <street>street1</street>  
        <city>city1</city>  
        <state>state1</state>  
        <zip>1</zip>  
      </ShipTo>  
      <ShipTo country="US">  
        <name>name2</name>  
        <street>street2</street>  
        <city>city2</city>  
        <state>state2</state>  
        <zip>-79228162514264337593543950335</zip>  
      </ShipTo>  
      <BillTo country="US">  
        <name>name1</name>  
        <street>street1</street>  
        <city>city1</city>  
        <state>state1</state>  
        <zip>1</zip>  
      </BillTo>  
    </PurchaseOrder>  
    ```  
  
## Vedere anche  
 [Utilizzo di dati XML](../xml-tools/working-with-xml-data.md)