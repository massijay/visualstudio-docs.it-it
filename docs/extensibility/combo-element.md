---
title: "Elemento casella combinata | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento casella combinata (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, casella combinata"
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Elemento casella combinata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce i comandi che vengono visualizzati in una casella combinata. Esistono quattro tipi di caselle combinate, come indicato di seguito: DropDownCombo, DynamicCombo, IndexCombo e MRUCombo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|  
|defaultWidth|Obbligatorio. Valore intero che specifica una larghezza in pixel della casella combinata.|  
|idCommandList|Obbligatorio. Un ID che viene inviato alla destinazione comando attiva per recuperare l'elenco di elementi da visualizzare nella casella combinata. L'ID sarà nello stesso ambito GUID del controllo.|  
|priority|Parametro facoltativo. Un valore numerico che specifica la priorità.|  
|tipo|Parametro facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non è specificato, utilizza pulsante.<br /><br /> DropDownCombo<br /> Il package VS è responsabile della compilazione nel contenuto di questa casella combinata. L'utente non può specificare qualsiasi elemento nella casella di testo di questo elenco a discesa.<br /><br /> DynamicCombo<br /> Il package VS è responsabile della compilazione nel contenuto di questa casella combinata. L'utente può modificare questo combinata e anche selezionare elementi in essa contenuti.<br /><br /> IndexCombo<br /> Lo stesso come DynamicCombo la differenza che genera l'indice dell'elemento anziché il testo.<br /><br /> MRUCombo<br /> Compilati dall'ambiente di sviluppo integrato (IDE) per conto di VSPackage.  L'utente può modificare in questa casella combinata. Nell'IDE vengono mantenuti fino alle ultime 16 voci per ogni casella combinata.<br /><br /> Quando l'utente seleziona un elemento nella casella combinata o immette un nuovo valore, l'IDE di notifica a VSPackage appropriato.|  
|Condizione|Parametro facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Padre|Parametro facoltativo. L'elemento padre del pulsante.|  
|CommandFlag|Obbligatorio. Vedere [comando Flag elemento](../extensibility/command-flag-element.md). I valori CommandFlag validi per un pulsante sono come indicato di seguito.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -Filtro tasti<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Stringhe|Obbligatorio. Vedere [stringhe elemento](../extensibility/strings-element.md). L'elemento ButtonText figlio deve essere definito.|  
|Annotazione|Commento facoltativo.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Commands](../extensibility/commands-element.md)|Rappresenta la raccolta di comandi sulla barra degli strumenti VSPackage.|  
  
## <a name="example"></a>Esempio  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella di comandi di Visual Studio (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)