---
title: "Procedura: Aggiungere comandi a menu di scelta rapida"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "menu di Office, creazione"
  - "sviluppo per Office in Visual Studio, menu di scelta rapida"
ms.assetid: 9a848817-db11-4294-8f6f-9181ab87aadd
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Procedura: Aggiungere comandi a menu di scelta rapida
  Questo argomento illustra come aggiungere comandi a un menu di scelta rapida in un'applicazione di Office con un componente aggiuntivo VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### Per aggiungere comandi al menu di scelta rapida in Office  
  
1.  Aggiungere un elemento **Barra multifunzione \(XML\)** in un progetto di componente aggiuntivo VSTO o a livello di documento. Per altre informazioni, vedere [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md). In  
  
2.  **Esplora soluzioni** selezionare **ThisAddin.cs** o **ThisAddin.vb**.  
  
3.  Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
     Il file di classe **ThisAddin** viene aperto nell'editor di codice.  
  
4.  Aggiungere il codice seguente alla classe **ThisAddIn**. Questo codice esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe XML della barra multifunzione all'applicazione di Office.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/thisaddin.vb#1)]  
  
5.  In **Esplora soluzioni** selezionare il file XML della barra multifunzione. Per impostazione predefinita, il file XML della barra multifunzione è denominato Ribbon1.xml.  
  
6.  Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
     Il file XML della barra multifunzione viene aperto nell'editor di codice.  
  
7.  Nell'editor di codice aggiungere codice XML che descriva il menu di scelta rapida e il controllo da aggiungere al menu di scelta rapida.  
  
     Nell'esempio seguente viene aggiunto un pulsante, un controllo e un controllo della raccolta al menu di scelta rapida per un documento di Word. L'ID del controllo di questo menu di scelta rapida è ContextMenuText. Per un elenco completo degli ID dei controlli del menu di scelta rapida di Office 2010, vedere [File della Guida di Office 2010: Identificatori del controllo dell'interfaccia utente Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui"> <contextMenus> <contextMenu idMso="ContextMenuText"> <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" /> <menu id="MySubMenu" label="My Submenu" > <button id="MyButton2" label="Button on submenu" /> </menu> <gallery id="galleryOne" label="My Gallery"> <item id="item1" imageMso="HappyFace" /> <item id="item2" imageMso="HappyFace" /> <item id="item3" imageMso="HappyFace" /> <item id="item4" imageMso="HappyFace" /> </gallery> </contextMenu> </contextMenus> </customUI>  
    ```  
  
8.  In **Esplora soluzioni** scegliere **MyRibbon.cs** o **MyRibbon.vb**.  
  
9. Aggiungere un metodo di callback alla classe `Ribbon1` per ogni controllo da gestire.  
  
     Il metodo di callback seguente consente di gestire il pulsante **My Button**. Questo codice aggiunge una stringa al documento attivo in corrispondenza della posizione corrente del cursore.  
  
     [!code-csharp[Trin_WordAddIn_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/ribbon1.cs#2)]
     [!code-vb[Trin_WordAddIn_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/ribbon1.vb#2)]  
  
## Vedere anche  
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Procedura dettagliata: creazione di menu di scelta rapida per segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Personalizzazione di menu di scelta rapida in Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  