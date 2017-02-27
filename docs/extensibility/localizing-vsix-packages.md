---
title: "Localizzazione di pacchetti VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "localizzazione del pacchetto"
  - "localizzazione dell'estensione"
  - "distribuzione localizzata"
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Localizzazione di pacchetti VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile localizzare un pacchetto VSIX creando un file Extension. vsixlangpack per ogni lingua di destinazione e quindi inserirli nella cartella corretta. Quando viene installato un pacchetto di aggiornamento, viene visualizzato il nome localizzato dell'estensione con una descrizione localizzata. Se si specifica un file di licenza localizzato, o un URL che punta alle informazioni localizzate, vengono anche visualizzate.  
  
 Se il contenuto del pacchetto VSIX include un package VS che aggiunge i comandi di menu o altra interfaccia utente, vedere [Localizzazione di comandi di Menu](../extensibility/localizing-menu-commands.md) per informazioni sulla localizzazione i nuovi elementi dell'interfaccia utente.  
  
## Struttura di directory  
 Quando un utente installa un'estensione **estensioni e aggiornamenti** controlla il livello principale del pacchetto VSIX per una cartella il cui nome corrispondente alle impostazioni internazionali di Visual Studio del computer di destinazione. Se **estensioni e aggiornamenti** trova una con estensione vsixlangpack file nella cartella, sostituisce i valori localizzati in tale file per i valori corrispondenti nel file vsixmanifest. Questi valori vengono visualizzati quando viene installato l'estensione. Nell'esempio seguente mostra la struttura di directory per un pacchetto VSIX che è localizzato in spagnolo \(es\-ES\) e francese \(fr\-FR\).  
  
 MyExtension.dll  
  
 Extension. vsixmanifest  
  
 \[Content\_Types\]. Xml  
  
 es\-ES  
  
 Vsixlangpack  
  
 fr\-FR  
  
 Vsixlangpack  
  
> [!NOTE]
>  I modelli di progetto supportati VSIX il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Genera un manifesto VSIX e denominarlo source.extension.vsixmanifest. Quando Visual Studio compila il progetto, copiare il contenuto del file in Extension. vsixmanifest nel pacchetto VSIX.  
  
## Il File vsixlangpack  
 Il file vsixlangpack segue il [lo Schema Language Pack VSIX](../extensibility/vsx-language-pack-schema-reference.md). Questo schema presenta un [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) elemento radice e i quattro elementi figlio: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [URL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), e [licenza](../extensibility/license-element-vsix-language-pack-schema.md). Tali elementi figlio corrispondano per il `Name`, `Description`, `MoreInfoURL`, e `License` gli elementi figlio del `Identifier` elemento del file Extension. vsixmanifest.  
  
 Quando si crea un file vsixlangpack, è necessario impostare il `Include in Vsix` proprietà `true`. In caso contrario, il testo di installazione localizzato verrà ignorato.  
  
#### Per impostare l'inclusione nella proprietà Vsix  
  
1.  In **Esplora**, il file vsixlangpack e quindi fare clic su **proprietà**.  
  
2.  Nella griglia delle proprietà, fare clic su **Includi in Vsix**, e impostarne il valore `true`.  
  
## Esempio  
  
### Descrizione  
 Nell'esempio seguente vengono illustrate parti rilevanti di un file Extension. vsixmanifest, insieme al file vsixlangpack corrispondente per lo spagnolo. I valori del language pack sostituiscono i valori dal manifesto se le impostazioni locali di Visual Studio del computer di destinazione sono impostata su spagnolo.  
  
### Codice  
 \[Extension. vsixmanifest\]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 \[Vsixlangpack\]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## Vedere anche  
 [Elemento Language Pack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Modello di progetto VSIX](../extensibility/vsix-project-template.md)