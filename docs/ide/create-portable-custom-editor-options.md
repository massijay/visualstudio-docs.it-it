---
title: Creare impostazioni personalizzate e portabili per l&quot;editor con EditorConfig | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 29
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
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: f377ada139d9c0e8b01b640cf603cf349dc1c3c3
ms.lasthandoff: 03/27/2017

---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Creare impostazioni personalizzate e portabili per l'editor con EditorConfig
In Visual Studio le impostazioni dell'editor di testo si applicano a tutti i progetti di un tipo specifico. Quindi, ad esempio, se si modifica un'impostazione dell'editor di testo C#, la modifica viene applicata a *tutti* i progetti C# in Visual Studio. In alcuni casi, tuttavia, potrebbe essere necessario usare convenzioni diverse dalle preferenze personali per l'editor. I file di [EditorConfig](http://editorconfig.org/) consentono di usare tali convenzioni impostando per l'editor di testo opzioni comuni diverse a seconda del progetto. Le impostazioni di EditorConfig, contenute in un file con estensione editorconfig aggiunto alla codebase, sostituiscono le impostazioni globali di Visual Studio per l'editor di testo. Questo significa che è possibile usare codebase su misura con le impostazioni per l'editor di testo preferite. Per usare questa funzionalità in Visual Studio non è necessario alcun plug-in.

## <a name="coding-consistency"></a>Coerenza del codice
Le impostazioni nei file di EditorConfig consentono di mantenere stili di codifica e impostazioni coerenti nell'ambito un linguaggio, ad esempio lo stile dei rientri, l'ampiezza delle tabulazioni, i caratteri di fine riga, la codifica e altro ancora, in una codebase, indipendentemente dall'IDE o dall'editor in uso. Ad esempio, quando si scrive codice in C#, se la codebase ha una convenzione preferita in base alla quale i rientri sono sempre costituiti da cinque spazi, i documenti devono usare la codifica UTF-8 e ogni riga termina sempre con un CR/LF, è possibile configurare un file con estensione editorconfig a tale scopo.

Le convenzioni di codifica usate per i progetti personali possono essere diverse da quelle per i progetti del team. Si potrebbe ad esempio preferire che durante la scrittura di codice la pressione del tasto TAB aggiunga un carattere di tabulazione. Il team, tuttavia, potrebbe preferire per il rientro quattro spazi anziché un carattere di tabulazione. I file di EditorConfig risolvono questo problema consentendo di predisporre una configurazione per ogni scenario.

Dato che le impostazioni si trovano all'interno di un file nella codebase, seguono quest'ultima nei suoi spostamenti. Quando il file di codice viene aperto, le impostazioni dell'editor di testo vengono implementate, a condizione che l'editor sia compatibile con EditorConfig. Per altre informazioni sui file di EditorConfig, vedere il sito Web [EditorConfig.org](http://editorconfig.org/). Se si modificano molti file con estensione editorconfig, potrebbe risultare utile l'estensione [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig).

## <a name="override-editorconfig-settings"></a>Eseguire l'override delle impostazioni di EditorConfig
Quando si aggiunge un file con estensione editorconfig in una cartella della gerarchia di file, le impostazioni vengono applicate a tutti i file applicabili in tale livello e sotto di questo. Per eseguire l'override delle impostazioni di EditorConfig per un determinato progetto o una codebase specifica e usare valori diversi o di override rispetto al file con estensione editorconfig di livello superiore, è sufficiente aggiungere un file con estensione editorconfig al livello che si vuole modificare.

![Gerarchia di EditorConfig](~/ide/media/vside_editorconfig_hierarchy.png)

Le impostazioni del nuovo file con estensione editorconfig si applicheranno al livello in cui si trova e a tutti i file sottostanti.

## <a name="supported-settings"></a>Impostazioni supportate
L'editor in Visual Studio supporta i valori seguenti del set di opzioni di EditorConfig di base.
- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- radice
- [convenzioni di stile del codice](../ide/editorconfig-code-style-settings-reference.md)

Le impostazioni di EditorConfig sono supportate in tutti i linguaggi supportati da Visual Studio, ad eccezione dell'XML.

## <a name="example"></a>Esempio
Di seguito è riportato un esempio che mostra lo stato del rientro di un frammento di codice C# prima e dopo l'aggiunta di un file con estensione editorconfig al progetto. L'impostazione **Tabulazioni** nella finestra di dialogo **Opzioni** per l'editor di testo di Visual Studio è definita in modo che quando si preme il tasto TAB all'interno del codice vengono generati spazi.

![Impostazione della tabulazione dell'editor di testo](~/ide/media/vside_editorconfig_tabsetting.png)

Come previsto, premendo il tasto TAB sulla linea successiva la linea rientra per l'aggiunta di quattro spazi vuoti.

![Il codice prima dell'uso di EditorConfig](~/ide/media/vside_editorconfig_before.png)

In un nuovo file denominato .editorconfig aggiunto al progetto viene inserito quanto segue. L'impostazione `[*.cs]` indica che questa modifica verrà applicata solo ai file con estensione cs all'interno del progetto.

![File .editorconfig aggiunto al progetto](~/ide/media/vside_editorconfig_addconfig.png)

A questo punto, quando si preme il tasto TAB, si ottengono caratteri di tabulazione anziché spazi.

![TAB aggiunge caratteri di tabulazione](~/ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  L'aggiunta di un file con estensione editorconfig al progetto o alla codebase non sostituisce gli stili esistenti con quelli nuovi, che vengono applicati solo alle linee aggiunte successivamente. Se si rimuove un file con estensione editorconfig dal progetto o dalla codebase, per ripristinare le impostazioni globali come impostazioni dell'editor è necessario ricaricare i file di codice. Eventuali errori nel file con estensione editorconfig vengono segnalati nella finestra Errori in Visual Studio.

## <a name="support-editorconfig-for-your-language-service"></a>Supporto di EditorConfig per il servizio di linguaggio

Nella maggior parte dei casi, quando si implementa un servizio di linguaggio di Visual Studio, non è necessario alcun intervento aggiuntivo per supportare le proprietà universali di EditorConfig. L'editor principale individua e legge automaticamente il file con estensione editorconfig quando gli utenti aprono i file e imposta le opzioni appropriate per buffer di testo e visualizzazione. Tuttavia, alcuni servizi di linguaggio scelgono di usare un'opzione di visualizzazione testo contestuale appropriata anziché usare impostazioni globali per elementi quali tabulazioni e spazi quando un utente modifica o formatta il testo. In questi casi il servizio di linguaggio deve essere aggiornato in modo da supportare i file EditorConfig.

Nella tabella seguente sono elencate le modifiche necessarie per aggiornare un servizio di linguaggio in modo che supporti i file EditorConfig.

| Opzione globale specifica del linguaggio deprecata | Sostituzione di opzioni contestuali |
| :------------- | :------------- |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs o Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs | !textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) o !textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize o Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize | textBufferOptions.GetOptionValue(DefaultOptions. IndentSizeOptionId) o textView.Options.GetOptionValue(DefaultOptions. IndentSizeOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize o Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize | textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId) o textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId) |

# <a name="see-also"></a>Vedere anche
[Creare impostazioni personalizzate e portabili per l'editor con EditorConfig](create-portable-custom-editor-options.md)
