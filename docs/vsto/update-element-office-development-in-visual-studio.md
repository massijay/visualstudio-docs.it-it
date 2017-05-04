---
title: "Elemento &lt;update&gt; (sviluppo per Office in Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "update (elemento)"
  - "<update> (elemento)"
  - "manifesti dell'applicazione [sviluppo per Office in Visual Studio], elemento <update>"
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Elemento &lt;update&gt; (sviluppo per Office in Visual Studio)
  L'elemento `update` specifica l'intervallo utilizzato dalla soluzione per verificare la presenza di aggiornamenti.  
  
## Sintassi  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## Elementi e attributi  
 L'elemento `update` è obbligatorio e si trova nello spazio dei nomi `vstav3`.  
  
 L'elemento `update` dispone dei seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`enabled`|Obbligatorio.  Impostare enabled su uno dei seguenti valori:<br /><br /> -   **true** per verificare la presenza di aggiornamenti.<br />-   **false** per non verificare la presenza di aggiornamenti.|  
  
 L'elemento `update` dispone degli elementi figlio riportati di seguito.  
  
### expiration  
 L'elemento `expiration` è obbligatorio e si trova nello spazio dei nomi `vstav3`.  L'elemento specifica l'intervallo utilizzato dalla soluzione per verificare la presenza di aggiornamenti.  
  
 L'elemento `expiration` dispone dei seguenti attributi.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`maximumAge`|-   Obbligatorio.  Impostare su un intero.|  
|`unit`|Obbligatorio.  Impostare `unit` su uno dei seguenti valori:<br /><br /> -   **hours**<br />-   **days**<br />-   **weeks**|  
  
## Esempio per verificare sempre la presenza gli aggiornamenti  
  
### Descrizione  
 Nell'esempio di codice seguente viene illustrato un elemento `update` impostato affinché verifichi sempre la presenza gli aggiornamenti nelle soluzioni Office.  
  
### Codice  
  
```  
<vstav3:update enabled="true" />  
```  
  
## Esempio per impostare un intervallo di aggiornamento predefinito  
  
### Descrizione  
 Nell'esempio di codice seguente viene illustrato un elemento `update` in un manifesto di applicazione relativo a soluzioni Office.  Questo esempio di codice fa parte di un esempio più esaustivo fornito in [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Codice  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## Vedere anche  
 [Distribuzione di una soluzione Office utilizzando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Manifesti di applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  