---
title: "Elemento di Flag di comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento CommandFlag (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, CommandFlag"
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Elemento di Flag di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Modifica del relativo elemento padre.  
  
## Sintassi  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## Attributi ed elementi  
 Nella sezione seguente vengono descritti i valori di elemento valido.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
  
|Valore|Descrizione|  
|------------|-----------------|  
|AllowParams|Indica che gli utenti possono immettere i parametri di comando nel **comando** finestra quando si digita il nome canonico del comando.<br /><br /> Valida per: `Button`|  
|AlwaysCreate|Menu viene creato anche se non contiene né gruppi di pulsanti.<br /><br /> Valida per: `Menu`|  
|CaseSensitive|Le voci utente tra maiuscole e minuscole.<br /><br /> Valida per: `Combo`|  
|CommandWellOnly|Applicare questo flag se il comando non viene visualizzato il menu di primo livello e si desidera renderlo disponibile per la personalizzazione di altre shell, ad esempio, per l'associazione a tasti di scelta rapida. Dopo aver installato il pacchetto Visual Studio, è possibile personalizzare questi comandi aprendo il **Opzioni** la finestra di dialogo e quindi modificare la posizione di comando sotto il **ambiente tastiera** categoria. Questo flag non influisce sul posizionamento nel menu di scelta rapida, barre degli strumenti, i controller di menu o sottomenu.<br /><br /> Valida per: `Button`, `Combo`|  
|DefaultDisabled|Per impostazione predefinita, il comando è disabilitato se non è stato caricato il package VS che lo implementa o `QueryStatus` metodo non è stato chiamato.<br /><br /> Valida per: `Button`, `Combo`|  
|DefaultDocked|Ancorati per impostazione predefinita. Questa impostazione non si applica alle barre degli strumenti perché sono sempre ancorati.|  
|DefaultInvisible|Per impostazione predefinita, il comando è invisibile se non viene caricato il package VS che lo implementa o `QueryStatus` metodo non è stato chiamato.<br /><br /> È consigliabile che è combinato con il `DynamicVisibility` flag.<br /><br /> Valida per: `Button`, `Combo`, `Menu`|  
|DontCache|L'ambiente di sviluppo non memorizza nella cache il `QueryStatus` risultati del metodo per questo comando.<br /><br /> Per un menu, ciò indica un controller di menu non memorizzare nella cache il testo di voci di menu. Questo flag viene utilizzato quando il menu contiene gli elementi dinamici o elementi che dispongono di testo dinamico.<br /><br /> Valida per: `Button`, `Menu`|  
|DynamicItemStart|Indica l'inizio di un elenco dinamico. In questo modo l'ambiente compilare un elenco chiamando successivamente il `QueryStatus` metodo sugli elementi dell'elenco fino a quando non viene restituito il flag OLECMDERR\_E\_UNSUPPORTED. Ciò vale per gli elementi come utilizzati più di recente \(MRU\) gli elenchi e finestra.<br /><br /> Valida per: `Button`|  
|DynamicVisibility|La visibilità del comando può essere modificata tramite il `QueryStatus` \(metodo\) o tramite un GUID che viene incluso nel contesto di `VisibilityConstraints` sezione.<br /><br /> Si applica ai comandi che vengono visualizzati nei menu e barre degli strumenti finestra dello strumento, ma non sulle barre degli strumenti di primo livello che vengono visualizzati nella finestra principale. Gli elementi di livello superiore della barra degli strumenti possono essere disabilitati, ma non nascosti quando il flag OLECMDF\_INVISIBLE viene restituito dal `QueryStatus` metodo. I comandi della barra degli strumenti visualizzati sulle barre degli strumenti finestra dello strumento possono essere nascosta.<br /><br /> In un menu, questo flag indica inoltre che deve essere automaticamente nascosto quando tutti i relativi membri sono nascosti. Questo flag viene in genere assegnato a sottomenu perché menu di primo livello dispone già di questo comportamento.<br /><br /> Questo flag deve essere combinato con il `DefaultInvisible` flag.<br /><br /> Valida per: `Button`, `Combo`, `Menu`|  
|Filtro tasti|Vedere l'argomento di filtro chiavi in [Elemento casella combinata](../extensibility/combo-element.md).<br /><br /> Valida per: `Combo`|  
|FixMenuController|Se questo comando è posizionato su un controller di menu, il comando è sempre il valore predefinito; il comando è selezionato, ogni volta che viene selezionato il pulsante di menu controller stesso. Se il controller di menu dispone di `TextIsAnchorCommand` flag impostato, quindi il controller menu accetta inoltre il testo del comando che ha il `FixMenuController` flag.<br /><br /> Deve avere un solo comando in un controller di menu di `FixMenuController` flag. Se è contrassegnato in modo più di un comando, l'ultimo comando nel menu diventa la predefinita.<br /><br /> Valida per: `Button`|  
|IconAndText|Visualizza un'icona e testo nel menu e barra degli strumenti.<br /><br /> Valida per: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Funzionalità di completamento automatico è disabilitato.<br /><br /> Valida per: `Combo`|  
|NoButtonCustomize|Non consentire all'utente di personalizzare questo pulsante.<br /><br /> Valida per: `Button`, `Combo`|  
|NoKeyCustomize|Non abilitare la personalizzazione della tastiera.<br /><br /> Valida per: `Button`, `Combo`|  
|NoShowOnMenuController|Se questo comando è posizionato su un controller di menu, il comando non viene visualizzato nell'elenco a discesa.<br /><br /> Valida per: `Button`|  
|NotInTBList|Non viene visualizzato nell'elenco delle barre degli strumenti disponibili. Questo è valido solo per i tipi di menu della barra degli strumenti.<br /><br /> Valida per: `Menu`|  
|NoToolbarClose|L'utente non può chiudere la barra degli strumenti. Questo è valido solo per i tipi di menu della barra degli strumenti.<br /><br /> Valida per: `Menu`|  
|PICT|Mostra solo un'icona su una barra degli strumenti, ma solo il testo in un menu. Se non viene specificata alcuna icona, viene illustrato uno spazio vuoto selezionabile in una barra degli strumenti.<br /><br /> Valida per: `Button`|  
|PostExec|Esegue il comando non bloccante. L'ambiente di sviluppo rinvia l'esecuzione fino al completamento di tutte le query pre\-elaborazione.<br /><br /> Valida per: `Button`|  
|RouteToDocs|Il comando viene indirizzato al documento attivo.<br /><br /> Valida per: `Button`|  
|StretchHorizontally|Quando viene impostato questo flag, la larghezza diventa la larghezza minima per la casella combinata e se c'è spazio sulla barra degli strumenti, la casella combinata si estende per riempire lo spazio disponibile. Ciò si verifica solo se la barra degli strumenti è ancorata in senso orizzontale e solo una casella combinata nella barra degli strumenti è possibile utilizzare il flag \(il flag viene ignorato in tutto eccetto la prima casella combinata\).<br /><br /> Valida per: `Combo`|  
|TextMenuUseButton|Utilizzare il `ButtonText` campo per i menu. Il campo predefinito è `MenuText` se è specificato.<br /><br /> Valida per: `Button`|  
|TestoConsente di modificare|Il testo del comando o menu può essere modificato in fase di esecuzione, in genere tramite il `QueryStatus` metodo.<br /><br /> Valida per: `Button`, `Menu`|  
|TextChangesButton|Valida per: `Button`|  
|TextIsAnchorCommand|Per un controller di menu, il testo del menu è tratto dal comando predefinito \(ancoraggio\). Un comando di ancoraggio è l'ultimo comando selezionato o impostare un latch. Se questo flag non è impostato, il controller di menu utilizza il proprio `MenuText` campo. Tuttavia, facendo clic su controller di menu consente ancora l'ultimo comando selezionato da quest'ultimo.<br /><br /> Si consiglia combinare questo flag con la `TextChanges` flag.<br /><br /> Questo flag si applica solo ai menu di tipo MenuController o MenuControllerLatched.<br /><br /> Valida per: `Menu`|  
|TextMenuCtrlUseMenu|Utilizzare il `MenuText` campo nei controller di menu. Il campo predefinito è `ButtonText`.<br /><br /> Valida per: `Button`|  
|TextMenuUseButton|Utilizzare il `ButtonText` campo per i menu. Il campo predefinito è `MenuText` se è specificato.<br /><br /> Valida per: `Button`|  
|TextOnly|Mostrare solo testo in una barra degli strumenti o un menu ma nessuna icona anche se viene specificato l'icona.<br /><br /> Valida per: `Button`|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento di pulsanti](../extensibility/buttons-element.md)|Fornisce un gruppo per [Elemento Button](../extensibility/button-element.md) gli elementi.|  
|[Elemento menu](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un VSPackage.|  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)