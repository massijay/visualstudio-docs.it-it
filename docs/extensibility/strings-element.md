---
title: Stringhe elemento | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 9
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
ms.openlocfilehash: 86e0148d495914b1cb1c0f0d19125992930a9521
ms.lasthandoff: 02/22/2017

---
# <a name="strings-element"></a>Elemento di stringhe
L'elemento di stringhe deve contenere almeno un **ButtonText** elemento figlio. Tutti gli elementi figlio sono facoltativi. Ad esempio i caratteri XML non valido '/' e '<’ must="" be="" coded="" as="" entities=""></’>&amp;'e'&lt;' e così via).  
  
 Una e commerciale nella stringa di testo specifica il tasto di scelta rapida per il comando.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|language|Facoltativo. Language = ".".|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|ButtonText|Questo campo e i cinque campi di testo seguente in una definizione di comando consentono di specificare il testo visualizzato in diversi menu. Per impostazione predefinita, il `ButtonText` campo viene visualizzato nel controller di menu. Il `ButtonText` campo diventa l'impostazione predefinita anche se gli altri campi di testo sono vuoti. Il `ButtonText` campo non può essere vuoto, anche se vengono specificati altri campi di testo.|  
|ToolTipText|Il `ToolTipText` campo specifica il testo visualizzato nella descrizione comandi per una voce di menu.<br /><br /> Se il `ToolTipText` campo è vuoto, il `ButtonText` campo viene utilizzato.|  
|MenuText|Il `MenuText` campo specifica il testo visualizzato per un comando se si tratta del menu principale, una barra degli strumenti, in un menu di scelta rapida o in un sottomenu. Se il `MenuText` è vuoto, utilizza l'ambiente di sviluppo integrato (IDE) di `ButtonText` campo. Il `MenuText` campo può essere utilizzato anche per la localizzazione.<br /><br /> Per i menu di scelta rapida, il `MenuText` campo è il nome che viene visualizzato sulla barra degli strumenti, menu di scelta rapida che consente la personalizzazione del menu di scelta rapida nell'IDE. Pertanto, essere specifico nella quale nome il menu di scelta rapida. ad esempio, utilizzare "Menu di scelta rapida pacchetto Widget" anziché "Collegamento".<br /><br /> Se il `MenuText` campo non è specificato, il `ButtonText` campo viene utilizzato.|  
|CommandName|Il `CommandName` campo specifica il testo visualizzato nella categoria tastiera il **comandi** nella scheda il **Personalizza** la finestra di dialogo (disponibile facendo clic su **Personalizza** sul **strumenti** menu).|  
|CanonicalName|La lingua inglese `CanonicalName` campo specifica il nome del comando nel testo inglese che può essere immessi nel **comando** finestra per eseguire la voce di menu. L'IDE consente di rimuovere i caratteri che non sono lettere, cifre, caratteri di sottolineatura o punti. Questo testo viene quindi concatenato per il `ButtonText` campo per definire il comando. Ad esempio, **nuovo progetto** sul **File** menu diventa il comando, il file. NewProject.<br /><br /> Se la lingua inglese `CanonicalName` campo non è specificato, l'IDE utilizza il `ButtonText` campo e strisce tutte tranne lettere, cifre, caratteri di sottolineatura e punti. Ad esempio, il testo del pulsante "/ definire comandi..." diventa DefineCommands, in cui vengono rimossi la e commerciale, lo spazio e sui puntini di sospensione.<br /><br /> Se il `TextChanges` flag specificato e il testo del comando viene modificato, il comando corrispondente riconosciuto dal **comando** finestra non viene modificata, la forma canonica dell'originale rimane `ButtonText` o inglese `CanonicalName` campi.|  
|LocCanonicalName|Il `LocCanonicalName` campo si comporta come l'inglese `CanonicalName` campo ma consente di testo del comando localizzati essere specificato. È possibile specificare entrambi i campi canonici. Poiché l'IDE analizza solo il testo immesso nella **comando** finestra e lo associa a un comando, in inglese e il testo inglese può essere associato lo stesso comando.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Button](../extensibility/button-element.md)|Definisce un elemento che l'utente può interagire con.|  
|[Elemento menu](../extensibility/menu-element.md)|Definisce una singola voce di menu.|  
|[Elemento casella combinata](../extensibility/combo-element.md)|Definisce i comandi che vengono visualizzati in una casella combinata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella di comandi di Visual Studio (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
