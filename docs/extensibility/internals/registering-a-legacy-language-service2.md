---
title: "Registrazione di un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "registrazione, servizi di linguaggio"
  - "servizi di linguaggio, le informazioni del Registro di sistema"
  - "Registro di sistema, servizi di linguaggio"
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrazione di un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le sezioni seguenti forniscono elenchi di voci del Registro di sistema per la lingua diverse opzioni di servizio disponibile in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Nel seguente elenco di voci del Registro di sistema, *VS Reg radice* è uguale a HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*y*, dove *y* è il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numero di versione.  
  
## Voci del Registro di sistema per le opzioni di servizio di linguaggio  
 Il *VS Reg radice*\\Languages\\Language Services\\*nome di lingua* chiave può contenere i seguenti valori.  
  
|Nome|Tipo|Intervallo|Descrizione|  
|----------|----------|----------------|-----------------|  
|\(Predefinito\)|REG\_SZ|*\< GUID \>*|GUID del servizio di linguaggio.|  
|LangResID|REG\_DWORD|0x0\-0xffff|Stringa identificatore di risorsa \(ResID\) per il nome del testo localizzato del linguaggio.|  
|Pacchetto|REG\_SZ|*\< GUID \>*|GUID del VSPackage.|  
|ShowCompletion|REG\_DWORD|0\-1|Specifica se il **il completamento delle istruzioni** opzioni il **Opzioni** la finestra di dialogo sono abilitati.|  
|ShowSmartIndent|REG\_DWORD|0\-1|Specifica se l'opzione per selezionare **Smart** rientri nel **Opzioni** è attivata la finestra di dialogo.|  
|RequestStockColors|REG\_DWORD|0\-1|Specifica se personalizzato o i colori predefiniti vengono utilizzati per colorare le parole chiave.|  
|ShowHotURLs|REG\_DWORD|0\-1|Specifica se l'utente può fare clic su URL.|  
|Per impostazione predefinita gli URL Non attivo|REG\_DWORD|0\-1|Specifica l'impostazione iniziale per il **Consenti apertura URL con clic singolo** opzione il **Opzioni** la finestra di dialogo.|  
|DefaultToInsertSpaces|REG\_DWORD|0\-1|Specifica se il servizio di linguaggio ha "Inserisci spazi" come l'opzione di scheda predefinita.|  
|ShowDropdownBarOption|REG\_DWORD|0\-1|Abilita o disabilita il **barra di spostamento** opzione il **Opzioni** la finestra di dialogo che mostra o nasconde il **barra di spostamento**.|  
|Solo finestra di codice singolo|REG\_DWORD|0\-1|Abilita o disabilita il **nuova finestra** scelte nel **finestra** menu per un servizio di linguaggio.|  
|EnableAdvancedMembersOption|REG\_DWORD|0\-1|Abilita o disabilita un **Opzioni** impostazione della finestra di dialogo per **Nascondi membri avanzati**.|  
|Supporto CF\_HTML|REG\_DWORD|0\-1|Specifica se l'editor consente la copia e Incolla di dati HTML.|  
|EnableLineNumbersOption|REG\_DWORD|0\-1|Specifica se il **i numeri di riga** opzioni di **Opzioni** la finestra di dialogo è abilitata per un servizio di linguaggio.|  
|HideAdvancedMembersByDefault|REG\_DWORD|0\-1|Specifica se i membri avanzati, ad esempio campi privati sono nascoste negli elenchi di completamento.|  
|ShowBraceCompletion|REG\_DWORD|0\-1|Specifica se il **con parentesi graffe completamento** opzione il **Opzioni** è attivata la finestra di dialogo.|  
  
### Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## Voci del Registro di sistema per le opzioni del Debugger lingue  
 Il *VS Reg radice*\\Languages\\Language Services\\*nome di lingua*\\Debugger Languages\\*GUID*\\ chiave può includere i valori seguenti.  
  
|Nome|Tipo|Intervallo|Descrizione|  
|----------|----------|----------------|-----------------|  
|\(Predefinito\)|REG\_SZ|testo|Il valore predefinito può essere utilizzato per documentare il nome della lingua. Il nome di questa chiave è un GUID di un analizzatore di espressioni che è una voce corrispondente in *\< VS Reg radice \>*\\AD7Metrics\\Expression dell'analizzatore di espressioni.|  
  
### Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## Voci del Registro di sistema per le opzioni di strumenti dell'Editor  
 È possibile aggiungere chiavi del Registro di sistema nella chiave EditorToolsOptions per le pagine delle proprietà e i nodi di proprietà. Queste chiavi e i relativi valori identificano pagine delle proprietà nel **Opzioni** la finestra di dialogo \(nel **strumenti** menu\) che consentono di configurare il servizio di linguaggio. Nell'esempio seguente, *nome pagina* è il nome di una pagina delle proprietà, e *nome nodo* è il nome di un nodo nell'albero di **Opzioni** la finestra di dialogo. La voce di pagina e la voce di nodo devono essere specificati separatamente.  
  
|Nome|Tipo|Intervallo|Descrizione|  
|----------|----------|----------------|-----------------|  
|\(Predefinito\)|REG\_SZ|ResID|Il nome visualizzato localizzato di questa pagina di opzioni. Il nome può essere testo letterale o \#`nnn`, dove `nnn` è un ID risorsa stringa nella DLL del VSPackage specificato satellite.|  
|Pacchetto|REG\_SZ|*GUID*|Il GUID del package VS che implementa questa pagina di opzioni.|  
|Pagina|REG\_SZ|*GUID*|Il GUID della pagina delle proprietà per richiedere il VSPackage chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo. Se questa voce del Registro di sistema non è presente, la chiave del Registro di sistema descrive un nodo, non una pagina.|  
  
### Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## Voci del Registro di sistema per le opzioni di estensione nome File  
 La voce per l'estensione del file deve includere il punto iniziale, ad esempio ".myext".  
  
|Nome|Tipo|Intervallo|Descrizione|  
|----------|----------|----------------|-----------------|  
|\(Predefinito\)|REG\_SZ|*GUID*|GUID del servizio per il servizio di linguaggio predefinito per questo tipo di estensione nome file.|  
  
### Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## Voci del Registro di sistema per opzioni dell'Editor  
 Il *VS Reg radice*\\Editors chiave può contenere i seguenti valori:  
  
|Nome|Tipo|Intervallo|Descrizione|  
|----------|----------|----------------|-----------------|  
|\(Predefinito\)|REG\_SZ|""|Inutilizzate; è possibile inserire il nome per la documentazione.|  
|DefaultToolboxTab|REG\_SZ|""|Nome della scheda casella degli strumenti per impostare come predefinita quando l'editor è attivo.|  
|DisplayName|REG\_SZ|ResID|Nome da visualizzare nel **Apri con** la finestra di dialogo. Il nome è l'ID di risorsa di stringa o un nome nel formato standard.|  
|ExcludeDefTextEditor|REG\_DWORD|0\-1|Utilizzato per il **Apri con** comando di menu. Se non si desidera elencare l'editor di testo predefinito nell'elenco degli editor disponibili per un tipo di file specifico, impostare questo valore su 1.|  
|LinkedEditorGUID|REG\_SZ|*\< GUID \>*|Utilizzato per qualsiasi servizio di linguaggio che è possibile aprire un file con supporto per tabelle codici. Ad esempio, quando si apre un file con estensione txt utilizzando il **Apri con** comando, vengono fornite opzioni per l'utilizzo di editor del codice sorgente con e senza codifica.<br /><br /> Il GUID specificato nel nome della sottochiave è per factory editor codepage. il GUID collegato specificato in questa voce del Registro di sistema è per la factory editor regolari. Lo scopo di questa voce è che se l'IDE non si apre un file utilizzando l'editor predefinito, l'IDE tenterà di utilizzare l'editor successivo nell'elenco. Questo editor successivo non deve essere il factory editor codepage perché questa factory editor è fondamentalmente la stessa come factory editor che non è riuscita.|  
|Pacchetto|REG\_SZ|*\< GUID \>*|GUID VSPackage ResID del nome visualizzato.|  
  
### Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## Voci del Registro di sistema per le opzioni di visualizzazione logica  
 Il *VS Reg radice*\\Editors\\*Editor GUI \>*\\LogicalViews chiave può contenere i seguenti valori.  
  
|Nome|Tipo|Intervallo|Descrizione|  
|----------|----------|----------------|-----------------|  
|\(Predefinito\)|REG\_SZ||Non utilizzato.|  
|*\< GUID \>*|REG\_SZ|""|Chiave per le visualizzazioni logiche supportate. È possibile configurare tutti gli elementi in base alle esigenze. Il nome della voce del Registro di sistema è ciò che è importante, non il valore, è sempre una stringa vuota.|  
  
### Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## Voci del Registro di sistema per le opzioni di estensione dell'Editor  
 Il *VS Reg radice*\\Editors\\*Editor GUID*\\Extensions chiave può contenere i seguenti valori. L'estensione del nome file non include il periodo iniziale.  
  
|Nome|Tipo|Intervallo|Descrizione|  
|----------|----------|----------------|-----------------|  
|\(Predefinito\)|REG\_SZ||Non utilizzato.|  
|*\< ext \>*|REG\_DWORD|0\-0xffffffff|Priorità relativa delle estensioni. Se due o più lingue condividono la stessa estensione, viene scelta la lingua di priorità più alta.|  
  
 Inoltre, selezione predefinita dell'utente corrente per un editor viene archiviata in HKEY\_Current\_User\\Software\\Microsoft\\VisualStudio\\*y*\\Default Editors\\*ext*. Il GUID del servizio di linguaggio selezionato è nella voce personalizzata. Questo ha la precedenza per l'utente corrente.  
  
### Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## Voci del Registro di sistema per le opzioni di servizio gestiti pacchetto Framework lingue  
 Le voci del Registro di sistema seguenti sono specifiche per le classi del servizio gestito pacchetto language framework \(MPF\). Queste voci del Registro di sistema indicano il supporto del servizio di linguaggio per varie funzionalità di IntelliSense e per altri avanzate funzionalità di modifica.  
  
 Queste voci del Registro di sistema sono accessibili tramite la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
|Nome|Tipo|Intervallo|Descrizione|  
|----------|----------|----------------|-----------------|  
|CodeSense|REG\_DWORD|0\-1|Supporto per le operazioni di IntelliSense.|  
|MatchBraces|REG\_DWORD|0\-1|Supporto per la corrispondenza di coppie di lingue, ad esempio le parentesi graffe, parentesi aperte e parentesi quadre.|  
|Informazioni rapide|REG\_DWORD|0\-1|Supporto per l'operazione di informazioni rapide di IntelliSense.|  
|ShowMatchingBrace|REG\_DWORD|0\-1|Supporto per visualizzare la coppia di lingue corrispondenti nella barra di stato.|  
|MatchBracesAtCaret|REG\_DWORD|0\-1|Supporto per visualizzare le coppie corrispondenti di linguaggio, in genere tramite evidenziando i due elementi.|  
|MaxErrorMessages|REG\_DWORD|0\-n|Il numero massimo di errori che possono essere visualizzati nel **elenco errori** finestra.|  
|CodeSenseDelay|REG\_DWORD|0\-n|Il numero di millisecondi di ritardo prima dell'avvio di uno sfondo l'analisi per un'operazione di IntelliSense.|  
|EnableAsyncCompletion|REG\_DWORD|0\-1|Supporto per l'analisi in background.|  
|EnableCommenting|REG\_DWORD|0\-1|Il supporto per blocchi di testo selezionati come commento e implica inoltre il supporto per rimuovendo il testo selezionato.|  
|EnableFormatSelection|REG\_DWORD|0\-1|Supporto per la formattazione del testo, ad esempio il rientro automatico o regolare la posizione delle parentesi graffe.|  
|AutoOutlining|REG\_DWORD|0\-1|Supporto per la struttura \(aree che possono essere compressi\).|  
|MaxRegions|REG\_DWORD|0\-n|Il numero massimo di aree nascoste per ogni file.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## Vedere anche  
 [Lo sviluppo di un servizio di linguaggio](../../extensibility/internals/developing-a-legacy-language-service.md)