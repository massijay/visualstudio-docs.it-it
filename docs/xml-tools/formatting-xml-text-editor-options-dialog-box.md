---
title: "Formattazione, XML, Editor di testo, finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Formattazione, XML, Editor di testo, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo consente di specificare le impostazioni di formattazione dell'editor XML.È possibile accedere alla finestra di dialogo **Opzioni** dal menu **Strumenti**.  
  
> [!NOTE]
>  Queste impostazioni sono disponibili quando si seleziona la cartella **Editor di testo**, la cartella **XML** e quindi l'opzione **Formattazione** nella finestra di dialogo **Opzioni**.  
  
## Attributi  
 **Mantieni la formattazione manuale degli attributi**  
 Gli attributi non vengono riformattati.Questo è il valore predefinito.  
  
> [!NOTE]
>  Se gli attributi si trovano su più righe, l'editor fa rientrare ogni riga degli attributi in base al rientro dell'elemento padre.  
  
 **Allinea ogni attributo su una riga separata**  
 Allinea verticalmente il secondo attributo e i successivi in base al rientro del primo attributo.Il testo XML seguente è un esempio di come vengono allineati gli attributi.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```  
  
## Riformatta automaticamente  
 **Quando si incolla dagli Appunti**  
 Riformatta il testo XML incollato dagli Appunti.  
  
 **Al completamento del tag di fine**  
 Riformatta l'elemento quando il tag di fine è completato.  
  
## Contenuto misto  
 **Mantieni contenuto misto per impostazione predefinita**  
 Determina se l'editor riformatta o meno il contenuto misto.Per impostazione predefinita l'editor tenta di riformattare il contenuto misto, a meno che il contenuto non venga rilevato in un ambito `xml:space="preserve"`.  
  
 Se un elemento contiene una combinazione di testo e markup, il contenuto viene considerato misto.Di seguito viene riportato un esempio di elemento con contenuto misto.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## Vedere anche  
 [Proprietà dei documenti XML, finestra Proprietà](../xml-tools/xml-document-properties-properties-window.md)   
 [Componenti dell'editor XML](../xml-tools/xml-editor-components.md)