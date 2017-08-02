---
title: 'Procedura: Personalizzare menu e barre degli strumenti in Visual Studio | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
caps.latest.revision: 28
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0ca0020fa9025e57df874f8fa8b5eb41e63a8c29
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Procedura: personalizzare menu e barre degli strumenti in Visual Studio
È possibile personalizzare Visual Studio non solo aggiungendo e rimuovendo barre degli strumenti e menu nella barra dei menu, ma anche aggiungendo e rimuovendo comandi in una barra degli strumenti o menu specifico.  
  
> [!WARNING]
>  Dopo aver personalizzato una barra degli strumenti o un menu, verificare che la relativa casella di controllo rimanga selezionata nella finestra di dialogo **Personalizza**. In caso contrario, le modifiche non verranno mantenute dopo aver chiuso e riaperto Visual Studio.  
  
 **Contenuto dell'argomento:**  
  
-   [Aggiunta, rimozione o spostamento di un menu nella barra dei menu](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)  
  
-   [Aggiunta, rimozione o spostamento di una barra degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)  
  
-   [Personalizzazione di un menu o di una barra degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)  
  
-   [Reimpostazione di un menu o di una barra degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)  
  
##  <a name="bkmk_addmenu"></a>Aggiunta, rimozione o spostamento di un menu nella barra dei menu  
  
1.  Nella barra dei menu scegliere**Strumenti**, **Personalizza**.  
  
     Viene visualizzata la finestra di dialogo **Personalizza**.  
  
2.  Nella scheda **Comandi** lasciare selezionato il pulsante di opzione **Barra dei menu**, lasciare selezionata **Barra dei menu** nell'elenco accanto all'opzione e quindi eseguire una delle procedure indicate di seguito:  
  
    -   Per aggiungere un menu, selezionare il pulsante **Aggiungi nuovo menu** e il pulsante **Modifica selezione** e quindi assegnare un nome al menu che si vuole aggiungere.  
  
         ![Finestra di dialogo Personalizza che illustra come aggiungere un menu](~/ide/media/addmenu.png "AddMenu")  
  
    -   Per rimuovere un menu, selezionarlo nell'elenco **Controlli** e fare clic sul pulsante **Elimina**.  
  
    -   Per spostare un menu all'interno della barra dei menu, selezionarlo nell'elenco **Controlli** e fare clic sul pulsante **Sposta su** o **Sposta giù**.  
  
##  <a name="bkmk_addtoolbar"></a>Aggiunta, rimozione o spostamento di una barra degli strumenti  
  
1.  Nella barra dei menu scegliere**Strumenti**, **Personalizza**.  
  
     Viene visualizzata la finestra di dialogo **Personalizza**.  
  
2.  Nella scheda **Barra degli strumenti** seguire una delle procedure indicate di seguito:  
  
    -   Per aggiungere una barra degli strumenti, selezionare il pulsante **Nuovo**, specificare un nome per la barra degli strumenti da aggiungere e quindi fare clic sul pulsante **OK**.  
  
         ![Finestra di dialogo Personalizza che illustra come aggiungere una barra degli strumenti](~/ide/media/addtoolbar.png "AddToolbar")  
  
    -   Per rimuovere una barra degli strumenti personalizzata, selezionarla nell'elenco **Barre degli strumenti**e fare clic sul pulsante **Elimina**.  
  
        > [!IMPORTANT]
        >  È possibile eliminare le barre degli strumenti create, ma non quelle predefinite.  
  
    -   Per spostare una barra degli strumenti in una posizione di ancoraggio diversa, selezionarla nell'elenco **Barre degli strumenti**, fare clic sul pulsante **Modifica selezione** e quindi scegliere una posizione nell'elenco visualizzato.  
  
         È inoltre possibile trascinare una barra degli strumenti per il bordo sinistro e spostarla in qualsiasi punto dell'area di ancoraggio principale.  
  
        > [!NOTE]
        >  Per altre informazioni su come migliorare l'uso e l'accessibilità delle barre degli strumenti, vedere [Procedura: Impostare le opzioni di accessibilità IDE](../ide/reference/how-to-set-ide-accessibility-options.md).  
  
##  <a name="bkmk_customize"></a> Personalizzazione di un menu o di una barra degli strumenti  
  
1.  Nella barra dei menu scegliere**Strumenti**, **Personalizza**.  
  
     Viene visualizzata la finestra di dialogo **Personalizza**.  
  
2.  Nella scheda **Comandi** selezionare il pulsante di opzione per il tipo di elemento che si vuole personalizzare.  
  
3.  Nell'elenco relativo al tipo di elemento desiderato selezionare il menu o la barra degli strumenti da personalizzare, quindi eseguire una delle procedure indicate di seguito.  
  
    -   Per aggiungere un comando, selezionare il pulsante **Aggiungi comando**.  
  
         Nella finestra di dialogo **Aggiungi comando** scegliere un elemento dall'elenco **Categorie**, scegliere un elemento dall'elenco **Comandi** e quindi fare clic sul pulsante **OK**.  
  
         ![Finestra di dialogo Aggiungi comando in Visual Studio](~/ide/media/addcommand.png "AddCommand")  
  
    -   Per eliminare un comando, selezionarlo nell'elenco **Controlli** e fare clic sul pulsante **Elimina**.  
  
    -   Per riordinare i comandi, selezionarne uno nell'elenco **Controlli** e fare clic sul pulsante **Sposta su** o **Sposta giù**.  
  
    -   Per separare i comandi in gruppi, selezionarne uno nell'elenco **Controlli**, fare clic sul pulsante **Modifica selezione**e quindi scegliere **Inizia un gruppo** nel menu visualizzato.  
  
##  <a name="bkmk_reset"></a> Reimpostazione di un menu o una barra degli strumenti  
  
1.  Nella barra dei menu scegliere**Strumenti**, **Personalizza**.  
  
     Viene visualizzata la finestra di dialogo **Personalizza**.  
  
2.  Nella scheda **Comandi** selezionare il pulsante di opzione per il tipo di elemento che si vuole reimpostare.  
  
3.  Nell'elenco del tipo di elemento desiderato selezionare il menu o la barra degli strumenti da reimpostare.  
  
4.  Selezionare il pulsante **Modifica selezione** e scegliere **Reimposta** nel menu visualizzato.  
  
     È anche possibile reimpostare tutti i menu e le barre degli strumenti facendo clic sul pulsante **Reimposta tutto**.
