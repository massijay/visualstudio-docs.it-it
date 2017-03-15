---
title: Supporto per la barra di spostamento in un servizio di linguaggio Legacy | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 16
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
ms.openlocfilehash: 88636468da333fd9200f8661d88af6e7fdeedc59
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Supporto per la barra di spostamento in un servizio di linguaggio Legacy
Barra di spostamento nella parte superiore della visualizzazione dell'editor consente di visualizzare i tipi e membri nel file. In discesa a sinistra vengono visualizzati i tipi e membri vengono visualizzati in destra elenco a discesa. Quando l'utente seleziona un tipo, il punto di inserimento viene posizionato nella prima riga del tipo. Quando l'utente seleziona un membro, il punto di inserimento viene posizionato sulla definizione del membro. Le caselle di riepilogo a discesa vengono aggiornate per riflettere la posizione corrente del punto di inserimento.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Visualizzare e aggiornare la barra di spostamento  
 Per supportare la barra di spostamento, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>classe e implementare il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>(metodo).</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Quando il servizio di linguaggio ha una finestra del codice, la base <xref:Microsoft.VisualStudio.Package.LanguageService>un'istanza di <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, che contiene il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>oggetto che rappresenta la finestra del codice.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.LanguageService> Il <xref:Microsoft.VisualStudio.Package.CodeWindowManager>oggetto viene quindi assegnato un nuovo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>oggetto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> Il <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>metodo ottiene un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>oggetto.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Se viene restituita un'istanza del <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>(classe), il <xref:Microsoft.VisualStudio.Package.CodeWindowManager>chiamate di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>metodo per popolare l'oggetto interno vengono elencate e passa il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>dell'oggetto per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elenco a discesa della barra manager.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Elenco a discesa barra manager, a sua volta, chiama il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>metodo di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>oggetto per stabilire il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>oggetto che contiene le due barre di menu a discesa.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>  
  
 Quando si sposta il punto di inserimento, il <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>chiamate al metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>(metodo).</xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> La base <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>metodo chiama il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>metodo nella <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>classe per aggiornare lo stato della barra di spostamento.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Si passa un set di <xref:Microsoft.VisualStudio.Package.DropDownMember>gli oggetti a questo metodo.</xref:Microsoft.VisualStudio.Package.DropDownMember> Ogni oggetto rappresenta una voce nell'elenco a discesa.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Il contenuto della barra di spostamento  
 Barra di spostamento in genere include un elenco di tipi e un elenco di membri. L'elenco dei tipi include tutti i tipi disponibili nel file di origine corrente. I nomi dei tipi includono le informazioni dello spazio dei nomi completo. Di seguito è riportato un esempio di codice c# con due tipi:  
  
```c#  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Verrà visualizzato l'elenco di tipo `TestLanguagePackage.TestLanguageService` e `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 L'elenco di membri Visualizza i membri del tipo selezionato nell'elenco dei tipi disponibili. Utilizzando l'esempio di codice precedente, se `TestLanguagePackage.TestLanguageService` è il tipo è selezionato, l'elenco dei membri conterrà i membri privati `tokens` e `serviceName`. La struttura interna `Token` non viene visualizzata.  
  
 È possibile implementare l'elenco dei membri per specificare un nome di un membro in grassetto quando il punto di inserimento viene posizionato all'interno. Membri possono essere visualizzati anche nel testo in grigio che indica che non siano all'interno dell'ambito in cui è attualmente posizionato il punto di inserimento.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Abilita il supporto per la barra di spostamento  
 Per abilitare il supporto per la barra di spostamento, è necessario impostare il `ShowDropdownBarOption` parametro il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>attributo `true`.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Questo parametro imposta la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>proprietà.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> Per supportare la barra di spostamento, è necessario implementare l' <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>oggetto nel <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>  
  
 Nell'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>(metodo), se il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>è impostata su `true`, è possibile restituire un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>oggetto.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Se non viene restituito l'oggetto, la barra di spostamento non viene visualizzata.  
  
 Pertanto è possibile per il controllo necessario reimpostare mentre è aperta la visualizzazione dell'editor, è possibile impostare l'opzione per visualizzare la barra di spostamento dell'utente. L'utente deve chiudere e riaprire la finestra dell'editor prima che venga eseguita la modifica.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Implementazione del supporto per la barra di spostamento  
 Il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>metodo accetta due valori che rappresenta la selezione corrente in ogni elenco e due elenchi (uno per ogni elenco a discesa).</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Gli elenchi e i valori di selezione possono essere aggiornati, nel qual caso il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>metodo deve restituire `true` per indicare che gli elenchi sono stati modificati.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
 Come cambia la selezione nei tipi di elenco a discesa, l'elenco dei membri deve essere aggiornato per riflettere il nuovo tipo. Come illustrato nell'elenco dei membri può essere:  
  
-   L'elenco dei membri per il tipo corrente.  
  
-   Tutti i membri disponibili nell'origine dei file, ma con tutti i membri non di tipo corrente visualizzato nel testo inattivo. L'utente può ancora selezionare i membri inattivo, pertanto possono essere utilizzati per la navigazione rapida, ma il colore indica che non fanno parte del tipo selezionato.  
  
 Un'implementazione di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>metodo in genere esegue i passaggi seguenti:</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
1.  Ottenere un elenco di dichiarazioni corrente del file di origine.  
  
     Esistono diversi modi per popolare gli elenchi. Un approccio consiste nel creare un metodo personalizzato in una versione di <xref:Microsoft.VisualStudio.Package.LanguageService>(classe) che chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>metodo con un motivo di analisi personalizzato che restituisce un elenco di tutte le dichiarazioni.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> Un altro approccio è possibile chiamare il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>direttamente dal metodo di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>metodo con il motivo di analisi personalizzata.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Un terzo approccio è possibile memorizzare nella cache le dichiarazioni nel <xref:Microsoft.VisualStudio.Package.AuthoringScope>restituito dall'ultima operazione di analisi completo nella classe di <xref:Microsoft.VisualStudio.Package.LanguageService>classe e che da recuperare il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>(metodo).</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
2.  Inserire o aggiornare l'elenco dei tipi.  
  
     Il contenuto dell'elenco di tipi sia in grado di essere aggiornato quando l'origine è stata modificata o se si è scelto di modificare lo stile di testo dei tipi in base alla posizione del punto di inserimento corrente. Si noti che questa posizione viene passata per il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>(metodo).</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
3.  Determinare il tipo per selezionare nell'elenco dei tipi in base alla posizione del punto di inserimento corrente.  
  
     È possibile cercare le dichiarazioni che sono state ottenute nel passaggio 1 per trovare il tipo che include la posizione corrente del cursore e quindi cercare l'elenco di tipi per tale tipo determinare il relativo indice nell'elenco di tipi.  
  
4.  Inserire o aggiornare l'elenco dei membri in base al tipo selezionato.  
  
     L'elenco dei membri riflette gli elementi visualizzati nel **membri** elenco a discesa. Il contenuto dell'elenco di membri potrà dover essere aggiornate se l'origine è stato modificato o se si siano visualizzando solo i membri del tipo selezionato e il tipo selezionato è stato modificato. Se si sceglie di visualizzare tutti i membri nel file di origine, lo stile di testo di ogni membro nell'elenco deve essere aggiornato se il tipo selezionato è stato modificato.  
  
5.  Determinare il membro da selezionare nell'elenco dei membri in base alla posizione del punto di inserimento corrente.  
  
     Ricerca le dichiarazioni che sono state ottenute nel passaggio 1 per il membro che contiene la posizione corrente del cursore, quindi cercare l'elenco dei membri per il membro determinare il relativo indice nell'elenco dei membri.  
  
6.  Restituire `true` se sono state apportate modifiche per gli elenchi o le selezioni negli elenchi.
