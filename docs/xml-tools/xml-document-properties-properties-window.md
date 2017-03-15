---
title: "Propriet&#224; dei documenti XML, finestra Propriet&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Propriet&#224; dei documenti XML, finestra Propriet&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella finestra **Proprietà** vengono fornite le informazioni principali sul documento attivo nell'editor XML.Le proprietà disponibili variano in base al tipo di documento XML correntemente attivo.  
  
> [!NOTE]
>  Tutte le proprietà del documento XML vengono salvate nella soluzione.Di conseguenza, non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.  
  
 **Codifica**  
 La codifica dei caratteri per il file.Modificando questa proprietà si modifica anche l'attributo della codifica nella dichiarazione XML e viceversa.La nuova codifica verrà utilizzata per codificare il file quando viene salvato.  
  
 **Input**  
 Il documento di input associato al foglio di stile XSLT.Viene utilizzato tramite il comando **Mostral'output XSLT**.È possibile selezionare un documento utilizzando il pulsante Sfoglia \(**...**\).  
  
 Questa proprietà è visibile solo quando il file XSLT è correntemente attivo nella finestra dell'editor.  
  
 **Output**  
 Il file che viene generato durante la trasformazione di un documento XML.  
  
 Se un file non è specificato, verrà generato un nome file predefinito in base all'attributo `method` dell'elemento `xsl:output` che determina l'estensione del file.Il file predefinito si trova nella directory temporanea dell'utente corrente.  
  
 **Schemi**  
 Gli schemi da utilizzare per la convalida.Il pulsante consente di aprire la finestra di dialogo **Schemi XSD**, che può essere utilizzata per scegliere gli schemi desiderati.  
  
 È possibile anche immettere il percorso degli schemi.Se vengono specificati più schemi, ogni singolo percorso di schema deve essere racchiuso tra virgolette.  
  
 **Foglio di stile**  
 Il file XSLT che viene utilizzato per trasformare il documento quando si utilizza il comando **Mostra l'output XSLT**.Se il campo è vuoto quando si utilizza il comando **Mostra l'output XSLT**, l'editor utilizzerà il valore specificato nell'istruzione di elaborazione `xml-stylesheet` del documento o richiederà all'utente il nome del file.  
  
 Quando si modifica un file XSLT, questa proprietà può essere utilizzata per specificare che è necessario utilizzare un foglio di stile diverso se è stato scelto il comando **Mostra l'output XSLT** o **Debug XSLT**.Ad esempio, è possibile eseguire tale operazione quando si modifica un foglio di stile incluso in un foglio di stile padre.  
  
## Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)   
 [Componenti dell'editor XML](../xml-tools/xml-editor-components.md)