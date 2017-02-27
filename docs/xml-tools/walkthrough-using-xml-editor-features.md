---
title: "Procedura dettagliata: utilizzo delle funzionalit&#224; dell&#39;editor XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura dettagliata: utilizzo delle funzionalit&#224; dell&#39;editor XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nei passaggi della procedura dettagliata viene illustrato come creare un nuovo documento XML.Nella procedura dettagliata vengono inoltre utilizzate alcune delle funzionalità dell'editor XML che lo rendono particolarmente utile per la creazione di codice XML.  
  
> [!NOTE]
>  Prima di avviare la procedura dettagliata, salvare il file hireDate.xsd \(incluso di seguito in questo argomento\) sul computer locale.  
  
### Per creare un nuovo file XML e associarlo a uno schema XML  
  
1.  Dal menu **File**, scegliere **Nuovo**, quindi fare clic su **File**.  
  
2.  Scegliere **File XML** nel riquadro **Modelli**, quindi fare clic su **Apri**.  
  
     Viene aperto un nuovo file nell'editor.Il file contiene una dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Scegliere il pulsante Sfoglia \(**...**\) nel campo **Schemi** della finestra delle proprietà del documento.  
  
     Viene visualizzata la finestra di dialogo **Schemi XSD**.  
  
4.  Scegliere **Aggiungi**.  
  
     Viene visualizzata la finestra di dialogo **Apri schema XSD**.  
  
5.  Selezionare il file hireDate.xsd e fare clic su **Apri**.  
  
6.  Scegliere **OK**.  
  
     Lo schema XML è ora associato al documento XML.Lo schema XML viene utilizzato per convalidare il documento.Viene anche utilizzato da IntelliSense per inserire elementi validi nell'elenco dei membri.  
  
### Per aggiungere dati  
  
1.  Digitare `<` nel riquadro dell'editor.  
  
     Nell'elenco dei membri vengono visualizzati gli elementi possibili:  
  
    -   **\!\-\-** per aggiungere un commento.  
  
    -   **\!DOCTYPE** per aggiungere un tipo di documento.  
  
    -   **?** per aggiungere un'istruzione di elaborazione.  
  
    -   **employee** per aggiungere l'elemento radice.  
  
2.  Selezionare **\<\!\-\-** per aggiungere un nodo di tipo comment e premere INVIO.  
  
     L'editor inserisce un tag di fine comment e colloca il cursore tra i tag comment di inizio e di fine.  
  
3.  Digitare Verifica file XML.  
  
4.  Digitare `<` su una nuova riga, quindi scegliere **employee** dall'elenco dei membri.  
  
     L'editor aggiunge l'inizio di un elemento XML, `<employee`.A questo punto è possibile aggiungere attributi all'elemento o chiudere il tag di inizio digitando `>`.  
  
5.  Digitare `>` per chiudere il tag.  
  
6.  L'editor aggiunge il tag di fine.Il tag di fine viene aggiunto con una sottolineatura ondulata che indica un errore di convalida.La descrizione comando visualizza il messaggio: contenuto dell'elemento 'employee' incompleto.Previsto "Identificatore".  
  
7.  Digitare `<` e scegliere **Identificatore** dall'elenco dei membri.Digitare quindi `>`.  
  
     L'editor aggiunge l'elemento XML, `<ID></ID>`, e posiziona il cursore dopo il tag di inizio identificatore.  
  
8.  Digitare abc.  
  
     Il testo abc presenta una sottolineatura ondulata.La descrizione comando visualizza il messaggio: l'elemento 'identificatore' non ha un valore valido per il relativo tipo di dati.  
  
9. Fare clic con il pulsante destro del mouse e scegliere **Vai a definizione**.  
  
     Nell'editor viene aperto il file hireDate.xsd in una nuova finestra del documento e il cursore viene posizionato sulla definizione dell'elemento dello schema identificatore.  
  
10. Tornare al file XML e sostituire il testo abc con 123.  
  
     La sottolineatura ondulata e la descrizione comando sotto il valore identificatore dell'elemento vengono cancellati.La descrizione comando del tag di fine del dipendente visualizza il messaggio: contenuto dell'elemento 'employee' incompleto.Previsto 'hire\-date'.  
  
11. Posizionare il cursore dopo il tag di fine identificatore, digitare `<`, scegliere la data di assunzione dall'elenco dei membri, quindi digitare `>`.  
  
     L'editor aggiunge l'elemento XML, `<hire-date></hire-date>`, e posiziona il cursore dopo il tag di inizio data assunzione.  
  
12. Digitare 2003\-01\-10 per il valore della data.  
  
### Per formattare il documento XML  
  
1.  Scegliere il pulsante **Formatta documento** sulla barra degli strumenti dell'editor XML.  
  
     Il documento XML viene riformattato.  
  
### Per salvare il documento XML  
  
1.  Scegliere **Salva con nome** dal menu  **File**.  
  
     Viene visualizzata la finestra di dialogo **Salva file con nome**.Il nome file predefinito è "XMLFile1".  
  
2.  Immettere il nome del file e il percorso del documento XML, quindi scegliere **Salva**.  
  
## File hireDate.xsd  
 nella procedura dettagliata viene utilizzato il seguente file di schema.  
  
```  
<?xml version="1.0"?>  
<xs:schema attributeFormDefault="unqualified"  
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"  
     xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="employee">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ID" type="xs:unsignedShort" />  
        <xs:element name="hire-date" type="xs:date" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)