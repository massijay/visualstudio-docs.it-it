---
title: "Elemento Commands | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Commands"
helpviewer_keywords: 
  - "Elemento Commands (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, comandi"
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento Commands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Rappresenta la raccolta di comandi sulla barra degli strumenti VSPackage. La raccolta può avere fino a cinque sottosezioni, come indicato di seguito: menu, gruppi, i pulsanti, casella combinata e bitmap.  
  
 Ogni sottosezione elemento figlio, ad esempio, \< Menu \>, viene identificato da un ID univoco del comando che è un GUID e la coppia identificatore numerico. Il GUID identifica il set di comandi"" e viene utilizzato per raggruppare i comandi correlati logicamente. VSPackage deve definire un proprio set di comandi per evitare conflitti con gli ID di comando che sono definiti da altri VSPackage.  
  
## Sintassi  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|pacchetto|Un GUID che identifica il package VS che fornisce i comandi.<br /><br /> Ad esempio, creare un pacchetto \= "guidVsPackage1Pkg".|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento menu](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene le voci che definiscono i gruppi di comando in un VSPackage.|  
|[Elemento di pulsanti](../extensibility/buttons-element.md)|Raggruppa gli elementi Button.|  
|[Elemento di bitmap](../extensibility/bitmaps-element.md)|Raggruppa gli elementi di Bitmap.|  
|[Elemento casella combinata](../extensibility/combos-element.md)|Raggruppa gli elementi di casella combinata.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che fornisce un VSPackage all'IDE. I possibili elementi sono voci di menu, menu, barre degli strumenti e caselle combinate.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un [Commands Element](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)