---
title: "Procedura: modificare i file XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura: modificare i file XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML è il nuovo editor per file XML.Può essere utilizzato per un file XML autonomo o per un file associato a un progetto Visual Studio.L'editor XML è associato alle estensioni di file seguenti: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt e .vssettings.L'editor XML è inoltre associato a qualsiasi altro tipo di file per il quale non è stato registrato un editor specifico e che presenta un contenuto XML o DTD.  
  
> [!NOTE]
>  I documenti XHTML sono gestiti dall'editor HTML.  
  
### Per modificare un file XML  
  
1.  Fare doppio clic sul file che si desidera modificare.  
  
### Per aggiungere un nuovo file XML a un progetto  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
2.  Scegliere **File XML** dal riquadro **Modelli**.  
  
3.  Immettere il nome del file nel campo **Nome** e scegliere **Aggiungi**.  
  
     Il file XML viene aggiunto al progetto e aperto nell'editor XML.Il file contiene la dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### Per aggiungere un file XML esistente a un progetto  
  
1.  Scegliere **Aggiungi elemento esistente** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi elemento esistente**.  
  
2.  Scegliere un file XML e premere **Aggiungi**.  
  
### Per creare un nuovo file XML o XSLT  
  
1.  Scegliere **Nuovo** dal menu **File**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo file**.  
  
2.  Scegliere **File XML** per creare un nuovo file XML oppure scegliere **File XSLT** per creare un nuovo foglio di stile XSLT.  
  
3.  Scegliere **Apri**.  
  
### Per creare un progetto per i file XML  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
2.  Selezionare il linguaggio del codice desiderato, scegliere **Progetto vuoto**, quindi fare clic su **OK**.  
  
3.  Aggiunta di file XML al progetto.  
  
     L'editor XML individua gli schemi aggiunti al progetto e li utilizza per la convalida e IntelliSense in qualsiasi file XML, schema o file XSLT che vengono modificati mentre il progetto è aperto.  
  
## Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)   
 [Proprietà dei documenti XML, finestra Proprietà](../xml-tools/xml-document-properties-properties-window.md)   
 [Procedura: creare uno schema XML da un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)