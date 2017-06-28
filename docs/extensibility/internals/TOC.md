# [Componenti e funzionalità di Visual Studio SDK](inside-the-visual-studio-sdk.md)
# [Visual Studio Shell](visual-studio-shell.md)
# [Comandi, menu e barre degli strumenti](commands-menus-and-toolbars.md)
## [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](how-vspackages-add-user-interface-elements.md)
## [File Visual Studio Command Table (VSCT)](visual-studio-command-table-dot-vsct-files.md)
### [Creazione e modifica di file con estensione vsct](authoring-dot-vsct-files.md)
### [Progettazione di file (con estensione vsct) della tabella di comandi XML](designing-xml-command-table-dot-vsct-files.md)
### [Procedura: Creare un file con estensione vsct](how-to-create-a-dot-vsct-file.md)
### [Flag della riga di comando del compilatore VSCT](vsct-compiler-command-line-flags.md)
## [Posizionamento predefinito di comandi, gruppi e barre degli strumenti](default-command-group-and-toolbar-placement.md)
## [Comandi, menu e gruppi definiti dall'IDE](ide-defined-commands-menus-and-groups.md)
### [GUID e ID dei menu di Visual Studio](guids-and-ids-of-visual-studio-menus.md)
### [GUID e ID delle barre degli strumenti di Visual Studio](guids-and-ids-of-visual-studio-toolbars.md)
### [GUID e ID dei comandi di Visual Studio](guids-and-ids-of-visual-studio-commands.md)
## [Progettazione dei comandi](command-design.md)
### [Implementazione dei comandi](command-implementation.md)
### [Disponibilità dei comandi](command-availability.md)
### [Algoritmo di routing dei comandi](command-routing-algorithm.md)
### [Linee guida per il posizionamento dei comandi](command-placement-guidelines.md)
## [Ottimizzazione dei comandi di menu e barre degli strumenti](optimizing-menu-and-toolbar-commands.md)
## [Miglioramento della disponibilità dei comandi](making-commands-available.md)
## [Comandi e menu che usano assembly di interoperabilità](commands-and-menus-that-use-interop-assemblies.md)
### [Determinazione dello stato dei comandi in base agli assembly di interoperabilità](determining-command-status-by-using-interop-assemblies.md)
### [Contratti dei comandi negli assembly di interoperabilità](command-contracts-in-interop-assemblies.md)
### [Registrazione dei gestori dei comandi negli assembly di interoperabilità](registering-interop-assembly-command-handlers.md)
### [Uso degli assembly di interoperabilità di Visual Studio](using-visual-studio-interop-assemblies.md)
## [Routing dei comandi nei pacchetti VSPackage](command-routing-in-vspackages.md)
# [Pacchetti VSPackage](vspackages.md)
## [Definizione del percorso di file VSPackage nella shell di Visual Studio](specifying-vspackage-file-location-to-the-vs-shell.md)
## [Risorse nei pacchetti VSPackage](resources-in-vspackages.md)
## [Procedure consigliate per la sicurezza nei pacchetti VSPackage](best-practices-for-security-in-vspackages.md)
## [Registrazione di pacchetti VSPackage](registering-vspackages.md)
# [Finestre dei documenti](document-windows.md)
## [Tabella documenti in esecuzione](running-document-table.md)
### [Uso di RDT_ReadLock](rdt-readlock-usage.md)
### [Salvataggio permanente e tabella documenti in esecuzione](persistence-and-the-running-document-table.md)
## [Caricamento dei documenti ritardato](delayed-document-loading.md)
# [Estendibilità dei servizi di linguaggio legacy](legacy-language-service-extensibility.md)
## [Migrazione di un servizio di linguaggio Legacy](migrating-a-legacy-language-service.md)
## [Nozioni fondamentali sui servizi di linguaggio legacy](legacy-language-service-essentials.md)
## [Sviluppo di un servizio di linguaggio legacy](developing-a-legacy-language-service.md)
### [Modello di un servizio di linguaggio legacy](model-of-a-legacy-language-service.md)
### [Interfacce dei servizi di linguaggio legacy](legacy-language-service-interfaces.md)
### [Intercettazione dei comandi dei servizi di linguaggio legacy](intercepting-legacy-language-service-commands.md)
#### [Comandi importanti per i filtri dei servizi di linguaggio](important-commands-for-language-service-filters.md)
### [Registrazione di un servizio di linguaggio legacy2](registering-a-legacy-language-service2.md)
### [Elenco di controllo: Creazione di un servizio di linguaggio legacy](checklist-creating-a-legacy-language-service.md)
### [Funzionalità dei servizi di linguaggio legacy2](legacy-language-service-features2.md)
#### [Colorazione della sintassi in un servizio di linguaggio legacy](syntax-coloring-in-a-legacy-language-service.md)
##### [Implementazione della colorazione della sintassi](implementing-syntax-coloring.md)
##### [Procedura: Usare gli elementi colorabili incorporati](how-to-use-built-in-colorable-items.md)
##### [Elementi colorabili personalizzati](custom-colorable-items.md)
#### [Formattazione automatica in un servizio di linguaggio legacy](automatic-formatting-in-a-legacy-language-service.md)
#### [Informazioni sui parametri in un servizio di linguaggio legacy1](parameter-info-in-a-legacy-language-service1.md)
#### [Completamento delle istruzioni in un servizio di linguaggio legacy](statement-completion-in-a-legacy-language-service.md)
#### [Definizione della struttura e testo nascosto in un servizio di linguaggio legacy](outlining-and-hidden-text-in-a-legacy-language-service.md)
##### [Procedura: Fornire il supporto per la struttura in un servizio di linguaggio legacy](how-to-support-outlining-in-a-legacy-language-service.md)
##### [Procedura: Fornire il supporto per il testo nascosto in un servizio di linguaggio legacy](how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
##### [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
#### [Supporto dei servizi di linguaggio per il debug](language-service-support-for-debugging.md)
## [Implementazione di un servizio di linguaggio legacy1](implementing-a-legacy-language-service1.md)
### [Panoramica dei servizi di linguaggio legacy](legacy-language-service-overview.md)
### [Implementazione di un servizio di linguaggio legacy2](implementing-a-legacy-language-service2.md)
### [Registrazione di un servizio di linguaggio legacy1](registering-a-legacy-language-service1.md)
### [Scanner e parser dei servizi di linguaggio legacy](legacy-language-service-parser-and-scanner.md)
### [Procedura dettagliata: Creazione di un servizio di linguaggio legacy](walkthrough-creating-a-legacy-language-service.md)
### [Procedura dettagliata: Recupero di un elenco di frammenti di codice installati (implementazione legacy)](walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
### [Funzionalità dei servizi di linguaggio legacy1](legacy-language-service-features1.md)
#### [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](brace-matching-in-a-legacy-language-service.md)
#### [Aggiunta di commenti al codice in un servizio di linguaggio legacy](commenting-code-in-a-legacy-language-service.md)
#### [Proprietà personalizzate dei documenti in un servizio di linguaggio legacy](custom-document-properties-in-a-legacy-language-service.md)
#### [Definizione della struttura in un servizio di linguaggio legacy](outlining-in-a-legacy-language-service.md)
#### [Riformattazione del codice in un servizio di linguaggio legacy](reformatting-code-in-a-legacy-language-service.md)
#### [Supporto per i frammenti di codice in un servizio di linguaggio legacy](support-for-code-snippets-in-a-legacy-language-service.md)
#### [Informazioni sui parametri in un servizio di linguaggio legacy2](parameter-info-in-a-legacy-language-service2.md)
#### [Informazioni rapide in un servizio di linguaggio legacy](quick-info-in-a-legacy-language-service.md)
#### [Completamento dei membri in un servizio di linguaggio legacy](member-completion-in-a-legacy-language-service.md)
#### [Completamento delle parole in un servizio di linguaggio legacy](word-completion-in-a-legacy-language-service.md)
#### [Supporto per la finestra Auto in un servizio di linguaggio legacy](support-for-the-autos-window-in-a-legacy-language-service.md)
#### [Supporto per la barra di spostamento in un servizio di linguaggio legacy](support-for-the-navigation-bar-in-a-legacy-language-service.md)
#### [Colorazione della sintassi in un servizio di linguaggio legacy](syntax-colorizing-in-a-legacy-language-service.md)
#### [Convalida dei punti di interruzione in un servizio di linguaggio legacy](validating-breakpoints-in-a-legacy-language-service.md)
## [Supporto degli strumenti di esplorazione dei simboli](supporting-symbol-browsing-tools.md)
### [Procedura: Registrare una libreria con il gestore degli oggetti](how-to-register-a-library-with-the-object-manager.md)
### [Procedura: Esporre gli elenchi dei simboli forniti dalla libreria al gestore degli oggetti](how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
### [Procedura: Identificare i simboli in una libreria](how-to-identify-symbols-in-a-library.md)
# [Progetti](projects.md)
## [Generazione di un nuovo progetto: dietro le quinte, parte 1](new-project-generation-under-the-hood-part-one.md)
## [Generazione di un nuovo progetto: dietro le quinte, parte 2](new-project-generation-under-the-hood-part-two.md)
## [Tipi di progetto](project-types.md)
### [Nozioni fondamentali sui tipi di progetto](project-type-essentials.md)
### [Creazione di tipi di progetto](creating-project-types.md)
#### [Decisioni di progettazione relative al tipo di progetto](project-type-design-decisions.md)
#### [Elenco di controllo: Creazione di nuovi tipi di progetto](checklist-creating-new-project-types.md)
#### [Creazione di istanze di progetto tramite le factory di progetto](creating-project-instances-by-using-project-factories.md)
#### [Uso del framework di pacchetto gestito per implementare un tipo di progetto (C#)](using-the-managed-package-framework-to-implement-a-project-type-csharp.md)
#### [Registrazione di un tipo di progetto](registering-a-project-type.md)
#### [Salvataggio permanente dei progetti](project-persistence.md)
#### [Uso di MSBuild](using-msbuild.md)
### [Aggiunta di modelli di progetto e di elemento di progetto](adding-project-and-project-item-templates.md)
#### [Contesto di progetto](project-context.md)
#### [Priorità di progetto](project-priority.md)
#### [Progetto di file esterni](miscellaneous-files-project.md)
#### [Registrazione di modelli di progetto e di elemento](registering-project-and-item-templates.md)
#### [Aggiunta di elementi nelle finestre di dialogo Aggiungi nuovo elemento](adding-items-to-the-add-new-item-dialog-boxes.md)
#### [Aggiunta di directory nella finestra di dialogo Nuovo progetto](adding-directories-to-the-new-project-dialog-box.md)
#### [Aggiunta di directory nella finestra di dialogo Aggiungi nuovo elemento](adding-directories-to-the-add-new-item-dialog-box.md)
#### [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](ide-defined-commands-for-extending-project-systems.md)
#### [CATID per gli oggetti che vengono in genere usati per estendere i progetti](catids-for-objects-that-are-typically-used-to-extend-projects.md)
### [Apertura e salvataggio di elementi di progetto](opening-and-saving-project-items.md)
#### [Visualizzazione di file tramite il comando Apri file](displaying-files-by-using-the-open-file-command.md)
#### [Visualizzazione di file tramite il comando Apri con](displaying-files-by-using-the-open-with-command.md)
#### [Salvataggio di un documento standard](saving-a-standard-document.md)
#### [Salvataggio di un documento personalizzato](saving-a-custom-document.md)
#### [Scelta dell'editor da usare per aprire un file in un progetto](determining-which-editor-opens-a-file-in-a-project.md)
### [Gestione delle opzioni di configurazione](managing-configuration-options.md)
#### [Panoramica delle opzioni di configurazione](configuration-options-overview.md)
#### [Pagine delle proprietà](property-pages.md)
#### [Configurazione di soluzioni](solution-configuration.md)
#### [Oggetto di configurazione del progetto](project-configuration-object.md)
#### [Configurazione del progetto per la compilazione](project-configuration-for-building.md)
#### [Configurazione del progetto per la gestione della distribuzione](project-configuration-for-managing-deployment.md)
#### [Configurazione del progetto per l'output](project-configuration-for-output.md)
### [Supporto del controllo del codice sorgente](supporting-source-control.md)
#### [Modello per i pacchetti del controllo del codice sorgente](model-for-source-control-packages.md)
#### [Decisioni di progettazione relative al controllo del codice sorgente](source-control-design-decisions.md)
#### [Dettagli di configurazione del controllo del codice sorgente](source-control-configuration-details.md)
#### [Linee guida aggiuntive sul controllo del codice sorgente per progetti ed editor](additional-source-control-guidelines-for-projects-and-editors.md)
#### [Dettagli di runtime del controllo del codice sorgente](source-control-runtime-details.md)
### [Annidamento dei progetti](nesting-projects.md)
#### [Procedura: Implementare progetti annidati](how-to-implement-nested-projects.md)
#### [Considerazioni per lo scaricamento e il ricaricamento di progetti annidati](considerations-for-unloading-and-reloading-nested-projects.md)
#### [Supporto di procedure guidate per i progetti annidati](wizard-support-for-nested-projects.md)
#### [Implementazione della gestione dei comandi per i progetti annidati](implementing-command-handling-for-nested-projects.md)
#### [Applicazione di un filtro nella finestra di dialogo AddItem per i progetti annidati](filtering-the-additem-dialog-box-for-nested-projects.md)
### [Aggiornamento dei progetti](upgrading-projects.md)
### [Architettura dei tipi di progetto](project-types-architecture.md)
#### [Elementi di un modello di progetto](elements-of-a-project-model.md)
#### [Componenti di base del modello di progetto](project-model-core-components.md)
#### [Quando creare tipi di progetto](when-to-create-project-types.md)
#### [Gerarchie e selezione](hierarchies-and-selection.md)
##### [Gerarchie in Visual Studio](hierarchies-in-visual-studio.md)
##### [Selezione e valuta nell'IDE](selection-and-currency-in-the-ide.md)
##### [Oggetti del contesto di selezione](selection-context-objects.md)
##### [Commenti e suggerimenti per l'utente](feedback-to-the-user.md)
## [Sottotipi di progetto](project-subtypes.md)
### [Progettazione di sottotipi di progetto](project-subtypes-design.md)
### [Sequenza di inizializzazione dei sottotipi di progetto](initialization-sequence-of-project-subtypes.md)
### [Proprietà e metodi estesi dai sottotipi di progetto](properties-and-methods-extended-by-project-subtypes.md)
### [Salvataggio permanente dei dati nel file di progetto MSBuild](persisting-data-in-the-msbuild-project-file.md)
### [Interfaccia utente delle proprietà del progetto](project-property-user-interface.md)
### [Estensione del modello a oggetti del progetto di base](extending-the-object-model-of-the-base-project.md)
### [Aggiunta di elementi nella finestra di dialogo Aggiungi nuovo elemento](contributing-to-the-add-new-item-dialog-box.md)
## [Progetti Web](web-projects.md)
### [Nozioni fondamentali sui progetti Web](web-project-essentials.md)
### [Supporto per siti Web](web-site-support.md)
#### [Modelli di supporto per siti Web](web-site-support-templates.md)
#### [Attributi di supporto per siti Web](web-site-support-attributes.md)
## [Gestione della distribuzione specializzata](handling-specialized-deployment.md)
## [Aggiunta di elementi al modello di automazione](contributing-to-the-automation-model.md)
### [Panoramica del modello di automazione](automation-model-overview.md)
### [Automazione per i pacchetti VSPackage](providing-automation-for-vspackages.md)
### [Esposizione di oggetti di progetto](exposing-project-objects.md)
### [Definizione di modelli di progetto](project-modeling.md)
### [Esposizione di eventi in Visual Studio SDK](exposing-events-in-the-visual-studio-sdk.md)
### [Supporto dell'automazione per le pagine di opzioni](automation-support-for-options-pages.md)
### [Automazione per il codice](providing-automation-for-code.md)
### [Procedura: Fornire l'automazione per Windows](how-to-provide-automation-for-windows.md)
### [Uso del modello di automazione](using-the-automation-model.md)
### [Automazione per la configurazione e per gli oggetti SelectedItem](automation-for-configuration-and-selecteditem-objects.md)
# [Soluzioni](solutions.md)
## [Panoramica delle soluzioni](solutions-overview.md)
## [File della soluzione (con estensione sln)](solution-dot-sln-file.md)
## [File delle opzioni utente della soluzione (con estensione suo)](solution-user-options-dot-suo-file.md)
# [Estensione delle proprietà](extending-properties.md)
## [Panoramica della finestra Proprietà](properties-window-overview.md)
## [Criteri dei modelli e finestra Proprietà](template-policy-and-the-properties-window.md)
## [Campi e interfacce della finestra Proprietà](properties-window-fields-and-interfaces.md)
## [Elenco di oggetti della finestra Proprietà](properties-window-object-list.md)
## [Pulsanti della finestra Proprietà](properties-window-buttons.md)
## [Griglia di visualizzazione delle proprietà](properties-display-grid.md)
## [Supporto per le proprietà di configurazione e del progetto](support-for-project-and-configuration-properties.md)
# [Opzioni e pagine di opzioni](options-and-options-pages.md)
## [Creazione di pagine di opzioni](creating-options-pages.md)
# [Supporto per le impostazioni utente](support-for-user-settings.md)
# [Nozioni fondamentali sui servizi](service-essentials.md)
## [Elenco di servizi disponibili](list-of-available-services.md)
# [Estendibilità del debugger di Visual Studio](../debugger/TOC.md)
# [Controllo del codice sorgente](source-control.md)
## [Nozioni fondamentali sull'integrazione del controllo del codice sorgente](source-control-integration-essentials.md)
## [Panoramica dell'integrazione del controllo del codice sorgente](source-control-integration-overview.md)
### [Novità del controllo del codice sorgente](what-s-new-in-source-control.md)
## [Creazione di un plug-in del controllo del codice sorgente](creating-a-source-control-plug-in.md)
### [Introduzione ai plug-in del controllo del codice sorgente](getting-started-with-source-control-plug-ins.md)
#### [Procedura: Installare un plug-in del controllo del codice sorgente](how-to-install-a-source-control-plug-in.md)
#### [Novità della versione 1.3 dell'API del plug-in del controllo del codice sorgente](what-s-new-in-the-source-control-plug-in-api-version-1-3.md)
#### [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
##### [Eliminazione di file ~SAK](elimination-of-tilde-sak-files.md)
##### [Applicazione delle impostazioni attraverso più connessioni di progetto](application-of-settings-across-multiple-project-connections.md)
##### [Creazione di cartelle contenitore padre per le soluzioni](creating-parent-container-folders-for-solutions.md)
##### [Confronto facoltativo della cartella di progetto locale con l'archivio del controllo del codice sorgente](optional-comparison-of-local-project-folder-to-source-control-store.md)
##### [Rimozione delle informazioni del controllo del codice sorgente dai file con estensione proj e sln](removal-of-source-control-information-from-dot-proj-and-dot-sln-files.md)
### [Architettura dei plug-in del controllo del codice sorgente](source-control-plug-in-architecture.md)
### [Guida per il test dei plug-in del controllo del codice sorgente](test-guide-for-source-control-plug-ins.md)
#### [Area di test 1: Aggiungere o aprire elementi dal controllo del codice sorgente](test-area-1-add-to-open-from-source-control.md)
#### [Area di test 2: Recuperare elementi dal controllo del codice sorgente](test-area-2-get-from-source-control.md)
#### [Area di test 3: Estrarre o annullare l'estrazione](test-area-3-check-out-undo-checkout.md)
#### [Area di test 4: Archiviare](test-area-4-check-in.md)
#### [Area di test 5: Modificare il controllo del codice sorgente](test-area-5-change-source-control.md)
#### [Area di test 6: Eliminare](test-area-6-delete.md)
#### [Area di test 7: Condividere](test-area-7-share.md)
#### [Area di test 8: Cambio di plug-in](test-area-8-plug-in-switching.md)
## [Creazione di un pacchetto VSPackage di controllo del codice sorgente](creating-a-source-control-vspackage.md)
### [Introduzione ai pacchetti VSPackage di controllo del codice sorgente](getting-started-with-source-control-vspackages.md)
#### [Scelta di implementazione di un pacchetto VSPackage di controllo del codice sorgente](determining-whether-to-implement-a-source-control-vspackage.md)
### [Architettura dei pacchetti VSPackage di controllo del codice sorgente](source-control-vspackage-architecture.md)
### [Funzionalità dei pacchetti VSPackage di controllo del codice sorgente](source-control-vspackage-features.md)
#### [Registrazione e selezione (VSPackage di controllo del codice sorgente)](registration-and-selection-source-control-vspackage.md)
#### [Query Edit Query Save (VSPackage di controllo del codice sorgente)](query-edit-query-save-source-control-vspackage.md)
#### [Controllo Glyph (VSPackage di controllo del codice sorgente)](glyph-control-source-control-vspackage.md)
#### [Interfaccia utente personalizzata (VSPackage di controllo del codice sorgente)](custom-user-interface-source-control-vspackage.md)
### [Elementi di progettazione dei pacchetti VSPackage di controllo del codice sorgente](source-control-vspackage-design-elements.md)
#### [Struttura VSPackage (VSPackage di controllo del codice sorgente)](vspackage-structure-source-control-vspackage.md)
#### [Interfacce e servizi correlati (VSPackage di controllo del codice sorgente)](related-services-and-interfaces-source-control-vspackage.md)
#### [Servizi forniti (VSPackage di controllo del codice sorgente)](services-provided-source-control-vspackage.md)
# [Procedure guidate](wizards.md)
## [File (con estensione vsdir) di descrizione della directory dei modelli](template-directory-description-dot-vsdir-files.md)
## [File (con estensione vsz) della procedura guidata](wizard-dot-vsz-file.md)
## [Interfaccia della procedura guidata (IDTWizard)](wizard-interface-idtwizard.md)
## [Parametri di contesto](context-parameters.md)
## [Parametri personalizzati](custom-parameters.md)
# [Strumenti personalizzati](custom-tools.md)
## [Implementazione di generatori di file singoli](implementing-single-file-generators.md)
## [Registrazione di generatori di file singoli](registering-single-file-generators.md)
## [Esposizione di tipi nelle finestre di progettazione visiva](exposing-types-to-visual-designers.md)
# [Utilità VSSDK](vssdk-utilities.md)
## [Utilità RegPkg](regpkg-utility.md)
### [Risoluzione dei problemi di registrazione dei pacchetti RegPkg](troubleshooting-regpkg-package-registration.md)
## [Utilità CreatePkgDef](createpkgdef-utility.md)
## [Utilità CreateExpInstance](createexpinstance-utility.md)
## [Strumenti dei temi di colore](color-theming-tools.md)
### [Editor dei colori VSIX](vsix-color-editor.md)
### [Compilatore dei colori VSIX](vsix-color-compiler.md)
## [Strumenti per il servizio immagini](image-service-tools.md)
### [ManifestFromResources](manifest-from-resources.md)
### [ManifestToCode](manifest-to-code.md)
### [Visualizzatore della libreria di immagini](image-library-viewer.md)
# [Installazione di pacchetti VSPackage con Windows Installer](installing-vspackages-with-windows-installer.md)
## [Nozioni di base su Windows Installer](windows-installer-basics.md)
## [Scenari di installazione di pacchetti VSPackage](vspackage-setup-scenarios.md)
## [Creazione e modifica di un pacchetto di Windows Installer](authoring-a-windows-installer-package.md)
## [Rilevamento dei requisiti di sistema](detecting-system-requirements.md)
## [Gestione dei componenti](component-management.md)
## [Scelta della directory di installazione per un pacchetto VSPackage](choosing-the-installation-directory-for-a-vspackage.md)
## [Registrazione di pacchetti VSPackage](vspackage-registration.md)
## [Distribuzione dei tipi di progetto](deploying-project-types.md)
## [Procedura: Generare le informazioni del Registro di sistema per un programma di installazione](how-to-generate-registry-information-for-an-installer.md)
## [Comandi da eseguire dopo l'installazione](commands-that-must-be-run-after-installation.md)
## [Disinstallazione di un pacchetto VSPackage con Windows Installer](uninstalling-a-vspackage-with-windows-installer.md)
# [Microsoft Help Viewer SDK](microsoft-help-viewer-sdk.md)