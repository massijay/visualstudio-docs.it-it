---
title: "Procedura: generare un frammento XML da XML Schema | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura: generare un frammento XML da XML Schema
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML è in grado di generare frammenti XML da uno schema XSD \(XML Schema Definition Language\).Ad esempio, quando si crea un file XML, mentre si è posizionati accanto al nome dell'elemento, premere TAB per inserire nell'elemento i dati XML generati dalle informazioni sullo schema per quel determinato elemento.  
  
 Questa funzionalità è disponibile solo per gli elementi.È inoltre necessario rispettare le seguenti regole:  
  
-   All'elemento deve essere associato un tipo di schema, ovvero l'elemento deve essere valido in base a uno schema associato.Il tipo di schema non può essere astratto e il tipo deve contenere gli attributi e\/o gli elementi figlio obbligatori.  
  
-   L'elemento corrente nell'editor deve essere vuoto e senza attributi.Gli elementi seguenti, ad esempio, sono tutti validi:  
  
    -   `<Account`  
  
    -   `<Account>`  
  
    -   `<Account></Account>`  
  
-   Il cursore deve trovarsi immediatamente a destra del nome dell'elemento.  
  
 Il frammento generato contiene tutti gli attributi e gli elementi obbligatori.Se `minOccurs` è maggiore di uno, il numero minimo richiesto di istanze di tale elemento è incluso nel frammento, fino a un massimo di 100 istanze. Qualsiasi valore fisso trovato nello schema comporta valori fissi nel frammento.Gli elementi `xsd:any` e `xsd:anyAttribute` vengono ignorati e non comportano costrutti di frammenti aggiuntivi.  
  
 I valori predefiniti vengono generati e specificati come valori modificabili.Se nello schema viene specificato un valore predefinito, verrà utilizzato tale valore.Tuttavia, se il valore predefinito dello schema è una striga vuota, l'editor genera i valori predefiniti nel modo seguente:  
  
-   Se il tipo di schema contiene facet di enumerazione, direttamente o indirettamente tramite un qualsiasi membro di tipo unione, il primo valore enumerato rilevato nel modello a oggetti dello schema viene utilizzato come valore predefinito.  
  
-   Se il tipo di schema è un tipo atomic, l'editor ottiene il tipo atomic e ne inserisce il nome.Per un tipo semplice derivato viene utilizzato il tipo base semplice.Per un tipo di elenco, il tipo atomic è l'attributo `itemType`.Per un tipo unione, il tipo atomic è il tipo atomic del primo `memberType`.  
  
## Esempio  
 Nei passaggi di questa sezione viene illustrato come utilizzare la funzionalità dei frammenti XML generati dallo schema dell'editor XML.  
  
> [!NOTE]
>  Prima di avviare tali procedure, salvare il file di schema nel computer locale.  
  
#### Per creare un nuovo file XML e associarlo a uno schema XML  
  
1.  Dal menu **File**, scegliere **Nuovo**, quindi fare clic su **File**.  
  
2.  Scegliere **File XML** nel riquadro **Modelli**, quindi fare clic su **Apri**.  
  
     Viene aperto un nuovo file nell'editor.Il file contiene una dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Scegliere il pulsante Sfoglia \(**...**\) nel campo **Schemi** della finestra delle proprietà del documento.  
  
     Viene visualizzata la finestra di dialogo **Schemi XSD**.  
  
4.  Scegliere **Aggiungi**.  
  
     Viene visualizzata la finestra di dialogo **Apri schema XSD**.  
  
5.  Selezionare il file di schema e fare clic su **Apri**.  
  
6.  Scegliere **OK**.  
  
     Lo schema XML è ora associato al documento XML.  
  
#### Per generare un frammento XML  
  
1.  Digitare `<` nel riquadro dell'editor.  
  
2.  Nell'elenco dei membri vengono visualizzati gli elementi possibili:  
  
     **\!\-\-** per aggiungere un commento.  
  
     **\!DOCTYPE** per aggiungere un tipo di documento.  
  
     **?** per aggiungere un'istruzione di elaborazione.  
  
     **Contatto** per aggiungere l'elemento radice.  
  
3.  Selezionare **Contatto** dall'elenco dei membri e premere INVIO.  
  
     L'editor aggiunge il tag di inizio `<Contact` e posiziona il cursore dopo il nome dell'elemento.  
  
4.  Premere TAB per generare i dati XML dell'elemento `Contact` in base alle informazioni sullo schema.  
  
### Input  
 Il seguente file di schema viene utilizzato nella procedura dettagliata.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xs:schema elementFormDefault="qualified"  
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:simpleType name="phoneType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Voice"/>  
      <xs:enumeration value="Fax"/>  
      <xs:enumeration value="Pager"/>  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:element name="Contact">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Name">  
          <xs:simpleType>  
            <xs:restriction base="xs:string"></xs:restriction>  
          </xs:simpleType>  
        </xs:element>  
        <xs:element name="Title"  
                    type="xs:string" />  
        <xs:element name="Phone"  
                    minOccurs="1"  
                    maxOccurs="unbounded">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Number"  
                          minOccurs="1">  
                <xs:simpleType>  
                  <xs:restriction base="xs:string"></xs:restriction>  
                </xs:simpleType>  
              </xs:element>  
              <xs:element name="Type"  
                          default="Voice"  
                          minOccurs="1"  
                          type="phoneType"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
### Output  
 Di seguito sono riportati i dati XML generati in base alle informazioni sullo schema associate all'elemento `Contact`.Gli elementi contrassegnati da `bold` indicano i campi modificabili nel frammento XML.  
  
```  
<Contact>  
  <Name>name</Name>  
  <Title>title</Title>  
  <Phone>  
    <Number>number</Number>  
    <Type>Voice</Type>  
  </Phone>  
</Contact>  
```  
  
## Vedere anche  
 [Frammenti di codice XML](../xml-tools/xml-snippets.md)   
 [Procedura: utilizzare frammenti XML](../xml-tools/how-to-use-xml-snippets.md)