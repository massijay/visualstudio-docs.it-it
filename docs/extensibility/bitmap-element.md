---
title: "Elemento di bitmap | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, bitmap"
  - "Elemento bitmap (VSCT XML schema)"
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento di bitmap
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce una bitmap. La bitmap viene caricata da una risorsa o da un file.  
  
## Sintassi  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|GUID|Obbligatorio. GUID dell'identificatore di comando\/ID GUID.<br /><br /> L'attributo guid per una bitmap non è associata a qualsiasi VSPackage o un altro gruppo di comando.  Deve essere univoco per la definizione della bitmap e non deve essere utilizzato per altri scopi.|  
|resID|ID dell'identificatore di comando\/ID GUID. È necessario il resID o l'attributo href.<br /><br /> L'attributo resID è un ID di risorsa di tipo integer che determina la striscia di bitmap che deve essere caricato durante l'unione di tabelle di comando.  Durante il caricamento di tabella del comando, le mappe di bit specificato dall'ID di risorsa verranno caricati dalla risorsa dello stesso modulo.|  
|usedList|Obbligatorio se è presente l'attributo resID. Consente di selezionare le immagini disponibili nell'elenco di bitmap.|  
|href|Percorso della bitmap. È necessario il resID o l'attributo href.<br /><br /> Il percorso di inclusione viene cercato il file di immagine indicato, che è incorporato nel file binario risulta.  Durante l'unione di tabelle di comando, l'immagine viene copiata ed è necessario alcuna ricerca delle risorse aggiuntive né carico.  Se l'attributo usedList non è presente, sono disponibili tutte le immagini nell'elenco. **Note:**  Le immagini possono essere fornite in vari formati che includono bmp, PNG e GIF.  Le versioni precedenti del compilatore non supportano le immagini bitmap a 32 bit che contiene informazioni alfa per la trasparenza parziale. La soluzione alternativa per queste versioni consiste nell'utilizzare il formato PNG.|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento di bitmap](../extensibility/bitmaps-element.md)|Raggruppa gli elementi di Bitmap.|  
  
## Esempio  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/>  
```  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)