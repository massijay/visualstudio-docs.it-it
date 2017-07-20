---
title: Sicurezza in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 7314921a9416184c4bd63312bd5a82cef4102ddd
ms.contentlocale: it-it
ms.lasthandoff: 05/30/2017

---
# Sicurezza in Visual Studio
<a id="security-in-visual-studio" class="xliff"></a>
È opportuno includere considerazioni sulla sicurezza in tutti gli aspetti dello sviluppo di applicazioni, dalla progettazione alla distribuzione. Iniziare eseguendo Visual Studio nel modo più sicuro possibile. Vedere [Autorizzazioni utente](../ide/user-permissions-and-visual-studio.md).  
  
 Per sviluppare applicazioni efficacemente sicure, è necessario acquisire familiarità con i concetti e le funzionalità relative alla sicurezza delle piattaforme per le quali si sviluppano le applicazioni. È inoltre necessario comprendere le tecniche di sicurezza del codice.  
  
## Informazioni sulla sicurezza
<a id="understanding-security" class="xliff"></a>  
 [Sicurezza](/dotnet/standard/security/index)  
 Vengono descritte la sicurezza dall'accesso di codice, la sicurezza basata sui ruoli e i criteri e gli strumenti di sicurezza di .NET Framework.  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877) (Dieci suggerimenti principali per la protezione del codice che ogni sviluppatore dovrebbe conoscere)  
 Vengono descritte le problematiche da tenere in considerazione per non compromettere i dati o il sistema.  
  
## Creazione di codice per la sicurezza
<a id="coding-for-security" class="xliff"></a>  
 La maggior parte degli errori di codifica che determinano vulnerabilità nella sicurezza si verificano perché gli sviluppatori compiono valutazioni errate rispetto all'input degli utenti o non hanno una comprensione globale della piattaforma per la quale sviluppano le applicazioni.  
  
 [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)  
 Vengono fornite indicazioni per la classificazione dei componenti finalizzata a risolvere i problemi di sicurezza.  
  
 [Procedure di sicurezza consigliate](/cpp/top/security-best-practices-for-cpp)  
 Vengono presi in esame i sovraccarichi del buffer e viene fornita una sintesi completa della funzionalità di controllo della sicurezza di Microsoft Visual C++ resa disponibile dal flag /GS della fase di compilazione.

## Compilazione di codice per la sicurezza
<a id="building-for-security" class="xliff"></a>  
 La sicurezza è anche un aspetto importante del processo di compilazione.  Alcuni passaggi aggiuntivi possono migliorare la sicurezza di un'app distribuita e impedire il reverse engineering non autorizzato, lo spoofing o attacchi di altro tipo.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Illustra come configurare e iniziare a usare la versione gratuita di PreEmptive Protection - Dotfuscator Community Edition per proteggere gli assembly .NET da attacchi di reverse engineering e da usi non autorizzati, ad esempio il debug non autorizzato.
  
 [Gestione delle firme di assembly e manifesti](managing-assembly-and-manifest-signing.md)  
 Illustra la firma con nome sicuro, che può essere usata per identificare in modo univoco i componenti software, impedendo così lo spoofing dei nomi.
