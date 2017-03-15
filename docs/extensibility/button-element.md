---
title: "Elemento Button | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento pulsanti (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, pulsanti"
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Elemento Button
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce un elemento che l'utente può interagire con. I pulsanti possono essere di tipi diversi: pulsante MenuButton e SplitDropDown.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|  
|priority|Parametro facoltativo. Un valore numerico che specifica la priorità.|  
|tipo|Parametro facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non è specificato, utilizza pulsante.<br /><br /> Pulsante<br /> Un comando standard che viene visualizzato sulla barra degli strumenti (in genere come un pulsante sotto forma di icona), menu e menu di scelta rapida.<br /><br /> MenuButton<br /> Una voce di menu che non viene eseguito un comando, ma produce un altro menu.<br /><br /> SplitDropDown<br /> Controlli, ad esempio i pulsanti Annulla e Ripeti sulla barra degli strumenti standard in Microsoft Word.|  
|Condizione|Parametro facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento padre](../extensibility/parent-element.md)|Parametro facoltativo. L'elemento padre del pulsante.|  
|[Icona elemento](../extensibility/icon-element.md)|Parametro facoltativo. L'icona associata al pulsante.|  
|[Elemento di Flag di comando](../extensibility/command-flag-element.md)|Obbligatorio. I valori CommandFlag validi per un pulsante sono come indicato di seguito.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TestoConsente di modificare<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Elemento di stringhe](../extensibility/strings-element.md)|Obbligatorio. L'elemento figlio [elemento ButtonText](../extensibility/buttontext-element.md) deve essere definito.|  
|Annotazione|Commento facoltativo.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento di pulsanti](../extensibility/buttons-element.md)|Raggruppa gli elementi Button.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente definisce un pulsante in un file vsct.  
  
 [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella di comandi di Visual Studio (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)