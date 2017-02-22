---
title: "&lt;Signature&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Signature> element [ClickOnce deployment manifest]"
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Signature&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene le informazioni necessarie per apporre una firma digitale al manifesto di distribuzione.  
  
## Sintassi  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## Note  
 L'applicazione di una firma protetta a un manifesto di distribuzione è un'operazione facoltativa ma consigliata.  Per ulteriori informazioni sulla firma di file XML, vedere la raccomandazione "XML\-Signature Syntax and Processing" del World Wide Web Consortium, descritta all'indirizzo [http:\/\/www.w3.org\/tr\/wsdl](http://www.w3.org/tr/wsdl) \(informazioni in lingua inglese\).  
  
 Se si desidera firmare il manifesto, è necessario che vengano forniti hash per tutti i file.  Un manifesto con file senza hash non può essere firmato, perché gli utenti non possono verificare il contenuto di file senza hash.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato un elemento `Signature` in un manifesto di distribuzione utilizzato in una distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## Vedere anche  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)