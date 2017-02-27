---
title: "CATID per gli oggetti che vengono in genere utilizzati per estendere i progetti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Package VS, CATID"
  - "GUID, package VS"
  - "CATID per i package VS"
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# CATID per gli oggetti che vengono in genere utilizzati per estendere i progetti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nella tabella seguente sono elencati i CATID utilizzati per estendere `Project` e gli oggetti di automazione di `ProjectItem` per [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]e i progetti[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .  questi CATID sono definiti in VSLangProj.olb.  
  
## Elenco di CATID  
  
|Nome|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614\-D0D5\-11D2\-8599\-006097 C68 E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615\-D0D5\-11D2\-8599\-006097 C68 E81}|  
  
## Visual Basic CATID  
 Nella tabella seguente sono elencati i CATID utilizzati per estendere gli oggetti di esplora [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  sono tutte definite in VSLangProj.olb.  
  
|Nome|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FD C879 \- C32 A\-4751\-A3D3\-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11\-14EB\-489b\-87F0\-F01 C52 AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D\-3 C72 \-40A5\-95A0\-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932D C619 \-2EAA\-4192\-B7E6\-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812\-8191\-4e81\-B7B3\-174045AB0 CB5}|  
  
## Visual c\# CATID  
 I seguenti CATID possono essere utilizzati per estendere gli oggetti di esplora [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .  sono tutte definite in VSLangProj.olb.  
  
|Nome|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{} 4EF9F003\-DE95\-4d60\-96B0\-212979F2A857|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12 CE10 A\-227F\-4963\-ADB6\-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF\-ED4E\-48B0\-8 C7 b C74 EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278\-054A\-45DB\-BF9E\-5F22484 CC84 C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8\- C855 \-4a4e\-95A5\- CB45 C67 D6 C27}|  
  
## C\+\+ CATID  
 Nell'sistema del progetto CATID di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] non viene esposto in librerie dei tipi in  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]di .NET 2003 e deve essere incluso nel codice ogni volta che si desidera estendere tali oggetti del progetto.  Questi CATID verranno inclusi nelle librerie dei tipi nelle versioni future di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Nome|GUID|  
|----------|----------|  
|`CVCProjectNode`|{} EE8299CB\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
|`CVCFolderNode`|{} EE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
|`CVCFileNode`|{EE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
  
 Nell'esempio di codice seguente viene illustrato come programmare questi CATID nel codice.  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Nell'sistema del progetto CATID di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] inoltre non viene esposto nelle librerie dei tipi in  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]di .NET 2003 e deve essere incluso nel codice ogni volta che si desidera estendere tali oggetti del progetto.  Questi CATID sono disponibili solo in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di .NET 2003 e non saranno disponibili nelle versioni successive di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Nome|GUID|  
|----------|----------|  
|`CVCAssemblyReferenceNode` **:**|{FE8299 C9 \-19B6\-4F20\-ABEA\-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE\-20A7\-48e4\-A CA1 \-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3\- C60 A\-44f4\-A74B\-14 C90 EF9CACE}|  
|`CVCReferences`|{} FE8299CA\-19B6\-4f20\-ABEA\-E1FD9A33B683|  
  
 Nell'esempio di codice seguente viene illustrato come programmare questi CATID nel codice:  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 I GUID per i tipi di progetto di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e di [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sono riportati nella tabella seguente.  
  
|Tipo di progetto|GUID|  
|----------------------|----------|  
|[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]|{FAE04E C0 \-301F\-11D3\-BF4B\-00 C04 F79EFBC}|  
|[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]|{F184B08F\- C81 C\-45F6\-A57F\-5ABD9991F28F}|  
  
## Vedere anche  
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)