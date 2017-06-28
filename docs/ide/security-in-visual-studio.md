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
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 57f7d51786d2636eb865eb81bb3468e79c6f19f9
ms.lasthandoff: 04/05/2017

---
# <a name="security-in-visual-studio"></a>Sicurezza in Visual Studio
È opportuno includere considerazioni sulla sicurezza in tutti gli aspetti dello sviluppo di applicazioni, dalla progettazione alla distribuzione. Iniziare eseguendo Visual Studio nel modo più sicuro possibile. Vedere [Autorizzazioni utente](../ide/user-permissions-and-visual-studio.md).  
  
 Per sviluppare applicazioni efficacemente sicure, è necessario acquisire familiarità con i concetti e le funzionalità relative alla sicurezza delle piattaforme per le quali si sviluppano le applicazioni. È inoltre necessario comprendere le tecniche di sicurezza del codice.  
  
## <a name="understanding-security"></a>Informazioni sulla sicurezza  
 [Sicurezza](http://msdn.microsoft.com/Library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)  
 Vengono descritte la sicurezza dall'accesso di codice, la sicurezza basata sui ruoli e i criteri e gli strumenti di sicurezza di .NET Framework.  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877) (Dieci suggerimenti principali per la protezione del codice che ogni sviluppatore dovrebbe conoscere)  
 Vengono descritte le problematiche da tenere in considerazione per non compromettere i dati o il sistema.  
  
## <a name="coding-for-security"></a>Creazione di codice per la sicurezza  
 La maggior parte degli errori di codifica che determinano vulnerabilità nella sicurezza si verificano perché gli sviluppatori compiono valutazioni errate rispetto all'input degli utenti o non hanno una comprensione globale della piattaforma per la quale sviluppano le applicazioni.  
  
 [Linee guida per la generazione di codice sicuro](http://msdn.microsoft.com/Library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)  
 Vengono fornite indicazioni per la classificazione dei componenti finalizzata a risolvere i problemi di sicurezza.  
  
 [Procedure di sicurezza consigliate](/cpp/top/security-best-practices-for-cpp)  
 Vengono presi in esame i sovraccarichi del buffer e viene fornita una sintesi completa della funzionalità di controllo della sicurezza di Microsoft Visual C++ resa disponibile dal flag /GS della fase di compilazione.

## <a name="building-for-security"></a>Compilazione di codice per la sicurezza  
 La sicurezza è anche un aspetto importante del processo di compilazione.  Alcuni passaggi aggiuntivi possono migliorare la sicurezza di un'app distribuita e impedire il reverse engineering non autorizzato, lo spoofing o attacchi di altro tipo.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Illustra come configurare e iniziare a usare la versione gratuita di PreEmptive Protection - Dotfuscator Community Edition per proteggere gli assembly .NET da attacchi di reverse engineering e da usi non autorizzati, ad esempio il debug non autorizzato.
  
 [Gestione delle firme di assembly e manifesti](managing-assembly-and-manifest-signing.md)  
 Illustra la firma con nome sicuro, che può essere usata per identificare in modo univoco i componenti software, impedendo così lo spoofing dei nomi.