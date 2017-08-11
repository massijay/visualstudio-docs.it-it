---
title: Modello di progetto Web Django per Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 242203505dc80c9cdfe6041fbf97308a16ccd2c8
ms.contentlocale: it-it
ms.lasthandoff: 07/18/2017

---

# <a name="django-web-project-template"></a>Modello di progetti Web Django

[Django](https://www.djangoproject.com/) è un framework Python di alto livello progettato per lo sviluppo rapido, sicuro e scalabile di applicazioni Web. Il supporto di Python in Visual Studio include un modello di progetto per configurare la struttura di un'applicazione Web basato su Django. Per usare il modello in Visual Studio, scegliere **File > Nuovo > Progetto**, cercare "Django" e selezionare il modello "Progetto Web Django". Il progetto risultante include il codice boilerplate, nonché un database SQLite predefinito. Il modello "Progetto Web Django vuoto" è simile ma non include il database.

Visual Studio offre il supporto IntelliSense completo per i progetti Django:

- Variabili di contesto passate nel modello:

    ![IntelliSense per le variabili di contesto](media/template-django-intellisense.png)

- Assegnazione di tag e filtro sia per variabili incorporate che per quelle definite dall'utente:

    ![IntelliSense per tag e filtri](media/template-django-intellisense-filter.png)

- Colorazione della sintassi per codice CSS e JavaScript incorporato:

    ![IntelliSense per CSS](media/template-django-intellisense-css.png)

    ![IntelliSense per JavaScript](media/template-django-intellisense-js.png)


Visual Studio offre anche [supporto completo per il debug](debugging.md) di progetti Django: 

![Punti di interruzione](media/template-django-debugging.png)

È normale che i progetti Django vengano gestiti usando il relativo file `manage.py` e questo è un presupposto a cui Visual Studio si attiene. Se si smette di usare tale file come punto di ingresso, praticamente si interrompe il file di progetto. In questo caso è necessario [ricreare il progetto da file esistenti](python-projects.md#creating-a-project-from-existing-files) senza contrassegnarlo come progetto Django.


## <a name="django-management-console"></a>Console di gestione Django

È possibile accedere alla console di gestione Django da vari comandi del menu **Progetto** oppure facendo clic con il pulsante destro del mouse sul progetto in Esplora soluzioni.

- **Apri shell Django**: apre una shell nel contesto dell'applicazione che consente di modificare i modelli.

    ![Console](media/template-django-console-shell.png)

- **DB sincronizzazione Django**: esegue `manage.py syncdb` in una finestra interattiva.

    ![Console](media/template-django-console-sync-db.png)

- **Raccogli file statici**: esegue `manage.py collectstatic --noinput` per copiare tutti i file statici nel percorso specificato da `STATIC_ROOT` nel file `settings.py`. Si noti che durante la [pubblicazione in Microsoft Azure](template-web.md#publishing-to-azure-app-service) l'operazione di pubblicazione include anche la raccolta automatica dei file statici.

    ![Console](media/template-django-console-collect-static.png)

- **Convalida**: esegue `manage.py validate`, che restituisce tutti gli errori di convalida presenti nei modelli installati specificati da `INSTALLED_APPS` nel file `settings.py`:

    ![Console](media/template-django-console-validate.png)
