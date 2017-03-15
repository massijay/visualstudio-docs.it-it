---
title: Associazione di tasti di scelta rapida a voci di Menu | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e75976be74d7d0362102a2cbeb32a85d3e612c67
ms.lasthandoff: 02/22/2017

---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Scelte rapide da tastiera di associazione di voci di Menu
Per associare un tasto di scelta rapida a un comando di menu personalizzati, è sufficiente aggiungere una voce al file vsct per il pacchetto. In questo argomento viene illustrato come eseguire il mapping di un tasto di scelta rapida per un pulsante personalizzato, voce di menu o comandi della barra e come applicare il mapping della tastiera nell'editor predefinito o limitati a un editor personalizzato.  
  
 Per assegnare i tasti di scelta rapida per voci di menu esistenti di Visual Studio, vedere [identificazione e personalizzazione di tasti](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Scelta di una combinazione di tasti  
 Molti tasti di scelta rapida sono già in uso in Visual Studio. È consigliabile non assegnare lo stesso collegamento a più di un comando perché associazioni duplicate sono difficili da rilevare e possono causare risultati imprevisti. Pertanto, è consigliabile verificare la disponibilità di un collegamento prima di assegnarlo.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Per verificare la disponibilità di un tasto di scelta rapida  
  
1.  Nel **Strumenti / opzioni / ambiente** finestra, selezionare **tastiera**.  
  
2.  Assicurarsi che **Usa nuova combinazione in** è impostato su **globale**.  
  
3.  Nel **premere i tasti di scelta rapida** , digitare il tasto di scelta rapida che si desidera utilizzare.  
  
     Se il collegamento è già utilizzato in Visual Studio, il **tasti di scelta attualmente utilizzato da** nella casella verrà visualizzato il comando che chiama attualmente il collegamento.  
  
4.  Provare diverse combinazioni di tasti fino a trovare quello che non è stato eseguito il mapping.  
  
    > [!NOTE]
    >  Tasti di scelta rapida che utilizzano ALT possono aprire un menu e non direttamente eseguire un comando. Pertanto, il **tasti di scelta attualmente utilizzato da** casella può essere vuota quando si digita un collegamento che include ALT. È possibile verificare che il collegamento non si apre un menu chiudendo il **opzioni** la finestra di dialogo e quindi premendo i tasti.  
  
 La procedura seguente si presuppone un VSPackage esistente con un comando di menu. Per assistenza durante questa operazione, dare un'occhiata [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Per assegnare un tasto di scelta rapida a un comando  
  
1.  Aprire il file vsct per il pacchetto.  
  
2.  Creare un oggetto vuoto `<KeyBindings>` sezione dopo la `<Commands>` se non è già presente.  
  
    > [!WARNING]
    >  Per ulteriori informazioni sui tasti di scelta rapida, vedere [Keybinding](../extensibility/keybinding-element.md).  
  
     Nel `<KeyBindings>` sezione, creare un `<KeyBinding>` voce.  
  
     Impostare il `guid` e `id` gli attributi a quelli del comando che si desidera richiamare.  
  
     Impostare il `mod1` attributo **controllo**, **Alt**, o **MAIUSC**.  
  
     La sezione KeyBindings dovrebbe essere simile al seguente:  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 Se il tasto di scelta rapida richiede più di due chiavi, impostare il `mod2` e `key2` gli attributi.  
  
 Nella maggior parte dei casi, **MAIUSC** non deve essere utilizzato senza un modificatore secondo perché premendo già si determina la maggior parte dei tasti alfanumerici in cui digitare una lettera maiuscola o un simbolo.  
  
 I codici tasto virtuale consentono di tasti speciali che non dispongono di un carattere associato, ad esempio, i tasti funzione e **BACKSPACE** chiave. Per ulteriori informazioni, vedere [Virtual-Key Codes](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Per rendere disponibile il comando di Visual Studio editor, impostare il `editor` attributo `guidVSStd97`.  
  
 Per rendere il comando è disponibile solo in un editor personalizzato, impostare il `editor` attributo sul nome dell'editor personalizzato di cui è stato generato da di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modello di pacchetto durante la creazione di package VS che include l'editor personalizzato. Per trovare il valore del nome, esaminare il `<Symbols>` sezione per una `<GuidSymbol>` nodo il cui `name` attributo termina con "`editorfactory`." Questo è il nome dell'editor personalizzato.  
  
## <a name="example"></a>Esempio  
 Questo esempio associa il tasto di scelta rapida CTRL + ALT + C per un comando denominato `cmdidMyCommand` in un pacchetto denominato `MyPackage`.  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>Esempio  
 Questo esempio associa il tasto di scelta rapida CTRL + B per un comando denominato `cmdidBold` in un progetto denominato `TestEditor`. Il comando è disponibile solo nell'editor personalizzato e non in altri editor.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione menu e comandi](../extensibility/extending-menus-and-commands.md)
