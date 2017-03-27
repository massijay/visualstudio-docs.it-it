---
title: Modello di progetto Web Django in Python Tools for Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 7f65641fbf15edfe16931badc19602a0fc773bff
ms.lasthandoff: 03/07/2017

---

# <a name="django-web-project-template"></a>Modello di progetti Web Django

[Django](https://www.djangoproject.com/) è un framework Python di alto livello progettato per lo sviluppo rapido, sicuro e scalabile di applicazioni Web. Python Tools for Visual Studio (PTVS) include un modello di progetto per configurare la struttura di un'applicazione Web basato su Django. Per usare il modello in Visual Studio, scegliere **File > Nuovo > Progetto**, cercare "Django" e selezionare il modello "Progetto Web Django". Il progetto risultante includerà il codice boilerplate, nonché un database SQLite predefinito. Il modello "Progetto Web Django vuoto" è simile ma non include il database.

PTVS offre il supporto IntelliSense completo per i progetti Django:

- Variabili di contesto passate nel modello:

    ![IntelliSense per le variabili di contesto](media/template-django-intellisense.png)

- Assegnazione di tag e filtro sia per variabili incorporate che per quelle definite dall'utente:

    ![IntelliSense per tag e filtri](media/template-django-intellisense-filter.png)

- Colorazione della sintassi per codice CSS e JavaScript incorporato:

    ![IntelliSense per CSS](media/template-django-intellisense-css.png)

    ![IntelliSense per JavaScript](media/template-django-intellisense-js.png)


PTVS offre inoltre [supporto completo per il debug](debugging.md) di progetti Django: 

![Punti di interruzione](media/template-django-debugging.png)

## <a name="django-management-console"></a>Console di gestione Django

È possibile accedere alla console di gestione Django tramite vari comandi del menu **Progetto** oppure facendo clic con il pulsante destro del mouse sul progetto in Esplora soluzioni.

- **Apri shell Django**: apre una shell nel contesto dell'applicazione che consente di modificare i modelli.

    ![Console](media/template-django-console-shell.png)

- **DB sincronizzazione Django**: esegue `manage.py syncdb` in una finestra interattiva.

    ![Console](media/template-django-console-sync-db.png)

- **Raccogli file statici**: esegue `manage.py collectstatic --noinput` per copiare tutti i file statici nel percorso specificato da `STATIC_ROOT` nel file `settings.py`. Si noti che durante la [pubblicazione in Microsoft Azure](template-web.md#publishing-to-azure-app-service) l'operazione di pubblicazione include anche la raccolta automatica dei file statici.

    ![Console](media/template-django-console-collect-static.png)

- **Convalida**: esegue `manage.py validate`, che restituisce tutti gli errori di convalida presenti nei modelli installati specificati da `INSTALLED_APPS` nel file `settings.py`:

    ![Console](media/template-django-console-validate.png)
