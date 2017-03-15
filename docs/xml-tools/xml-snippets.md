---
title: "Frammenti di codice XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Frammenti di codice XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML offre una funzionalità denominata *XML snippets*, che consente di compilare i file XML con maggiore rapidità.È possibile riutilizzare i frammenti di codice XML inserendoli nei file.È possibile inoltre generare dati XML basati su uno schema XSD \(XML Schema Definition Language\).  
  
## Frammenti di codice XML riutilizzabili  
 L'editor XML include diversi frammenti di codice che comprendono alcune delle attività più comunie che facilitano la creazione di file XML.Ad esempio, se si sta creando uno schema XML, utilizzando i frammenti "Elemento Sequence di tipo complesso" e "Elemento di tipo semplice" sarà possibile inserire il seguente testo XML nel file.Il valore `name` può quindi essere modificato in base alle esigenze.  
  
```  
<xs:element name="name">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="name">  
        <xs:simpleType>  
          <xs:restriction base="xs:string"></xs:restriction>  
        </xs:simpleType>  
      </xs:element>  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 È possibile inserire i frammenti di codice in due modi diversi:Il comando **Inserisci frammento** consente l'inserimento del frammento di codice XML nella posizione del cursore.Il comando **Racchiudi tra** consente di posizionare il frammento di codice XML attorno al testo selezionato.Entrambi i comandi sono disponibili dal sottomenu **IntelliSense** del menu **Modifica** o dal menu di scelta rapida dell'editor.  
  
 Per ulteriori informazioni, vedere [Procedura: utilizzare frammenti XML](../xml-tools/how-to-use-xml-snippets.md).  
  
## Frammenti di codice XML generati da uno schema  
 L'editor XML è in grado anche di generare un frammento di codice XML da uno schema XML.Tale funzionalità consente di inserire nell'elemento gli elementi XML generati dalle informazioni sullo schema per quel determinato elemento.  
  
 Per ulteriori informazioni, vedere [Procedura: generare un frammento XML da XML Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## Creazione di nuovi frammenti di codice XML  
 Oltre ai frammenti inclusi in [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio per impostazione predefinita, è possibile creare e utilizzare i frammenti di codice XML di propria creazione.  
  
 Per ulteriori informazioni, vedere [Procedura: creare frammenti XML](../xml-tools/how-to-create-xml-snippets.md).  
  
## Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)