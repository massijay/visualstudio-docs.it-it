---
title: "Elemento &lt;PackageFiles&gt; (programma di avvio automatico) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<PackageFiles> (elemento) [programma di avvio automatico]"
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# Elemento &lt;PackageFiles&gt; (programma di avvio automatico)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento `PackageFiles` contiene gli elementi `PackageFile`, che definiscono i package di installazione eseguiti in seguito all'utilizzo dell'elemento `Command`.  
  
## Sintassi  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## Elementi e attributi  
 L'elemento `PackageFiles` presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|Parametro facoltativo.  Se è impostato a `false`, il programma di installazione scaricherà solo file a cui viene fatto riferimento dall'elemento `Command`.  Se è impostato su `true`, verranno scaricati tutti i file.<br /><br /> Se è impostato su `IfNotHomesite`, il programma di installazione si comporterà come se fosse impostato su `False` se `ComponentsLocation` è impostato su `HomeSite` e, in caso contrario, si comporterà come se fosse impostato su `True`.  Questa impostazione può essere utile per consentire l'esecuzione di package che corrispondono a programmi di avvio in base al proprio comportamento in uno scenario HomeSite.<br /><br /> L'impostazione predefinita è `true`.|  
  
## PackageFile  
 L'elemento `PackageFile` è un elemento figlio di `PackageFiles`.  Un elemento `PackageFiles` deve contenere almeno un elemento `PackageFile`.  
  
 `PackageFile` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio.  Nome del file del package.  Si tratta del nome a cui l'elemento `Command` farà riferimento al momento della definizione delle condizioni di installazione di un package.  Questo valore viene utilizzato anche come chiave della tabella `Strings` per recuperare il nome localizzato che verrà utilizzato da strumenti quale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per la descrizione del package.|  
|`HomeSite`|Parametro facoltativo.  Percorso del package sul server remoto, se non è incluso nel programma di installazione.|  
|`CopyOnBuild`|Parametro facoltativo.  Specifica se il programma di avvio automatico deve copiare il file del pacchetto sul disco in fase di compilazione.  L'impostazione predefinita è true.|  
|`PublicKey`|Chiave pubblica crittografata del firmatario del certificato del package.  L'attributo è obbligatorio se viene utilizzato `HomeSite`, altrimenti è facoltativo.|  
|`Hash`|Parametro facoltativo.  Hash SHA1 del file del pacchetto.  Viene utilizzato per verificare l'integrità del file al momento dell'installazione.  Se non è possibile calcolare l'hash identico dal file di package, il package non verrà installato.|  
  
## Esempio  
 Nell'esempio di codice riportato di seguito vengono definiti package per il package ridistribuibile di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e le relative dipendenze, ad esempio Windows Installer.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## Vedere anche  
 [Elemento \<Product\>](../deployment/product-element-bootstrapper.md)   
 [Elemento \<Package\>](../deployment/package-element-bootstrapper.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)