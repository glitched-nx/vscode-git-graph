# Git Graph extension for Visual Studio Code

Fork of mhutchie's Git Graph with further improvements.
Main improvements:

* Selection of single branch and/or author. Can be activated with `git-graph.repository.singleBranchSelect` and `git-graph.repository.singleAuthorSelect`
* Added button to collapse commit summary (hansu#3)
* Added checkbox 'Allow unrelated histories' when merge action
* New setting `git-graph.toolbarButtonVisibility` to configure the visibility of some items of the toolbar. For example: `{"Remotes": true, "Simplify": true}
* Added simplifyByDecoration checkbox (hansu#33)
* Fix right clicks triggers native context menu on macOS (hansu#38)
* Added button to jump to HEAD (hansu#14)
* Added collapse/expand buttons to commit diff view (hansu#6)
* Resize column width without header (hansu#4)
* Added author filter (hansu#1)
* Added sticky header option (mhutchie#132)

![Additions](https://github.com/hansu/vscode-git-graph/raw/master/resources/demo.gif)

## How to Install

1. Download the latest release from https://github.com/hansu/vscode-git-graph/releases (download the .vsix file in the "Assets" section).

2. Run the VS-Code command "Extensions: Install from VSIX..."

## Features

* Git Graph View:
    * Display:
        * Local & Remote Branches
        * Local Refs: Heads, Tags & Remotes
        * Uncommitted Changes
    * Perform Git Actions (available by right clicking on a commit / branch / tag):
        * Create, Checkout, Delete, Fetch, Merge, Pull, Push, Rebase, Rename & Reset Branches
        * Add, Delete & Push Tags
        * Checkout, Cherry Pick, Drop, Merge & Revert Commits
        * Clean, Reset & Stash Uncommitted Changes
        * Apply, Create Branch From, Drop & Pop Stashes
        * View annotated tag details (name, email, date and message)
        * Copy commit hashes, and branch, stash & tag names to the clipboard
    * View commit details and file changes by clicking on a commit. On the Commit Details View you can:
        * View the Visual Studio Code Diff of any file change by clicking on it.
        * Open the current version of any file that was affected in the commit.
        * Copy the path of any file that was affected in the commit to the clipboard.
        * Click on any HTTP/HTTPS url in the commit body to open it in your default web browser.
    * Compare any two commits by clicking on a commit, and then CTRL/CMD clicking on another commit. On the Commit Comparison View you can:
        * View the Visual Studio Code Diff of any file change between the selected commits by clicking on it.
        * Open the current version of any file that was affected between the selected commits.
        * Copy the path of any file that was affected between the selected commits to the clipboard.
    * Code Review - Keep track of which files you have reviewed in the Commit Details & Comparison Views.
        * Code Review's can be performed on any commit, or between any two commits (not on Uncommitted Changes).
        * When a Code Review is started, all files needing to be reviewed are bolded. When you view the diff / open a file, it will then be un-bolded.
        * Code Reviews persist across Visual Studio Code sessions. They are automatically closed after 90 days of inactivity.
    * View uncommitted changes, and compare the uncommitted changes with any commit.
    * Hover over any commit vertex on the graph to see a tooltip indicating:
        * Whether the commit is included in the HEAD.
        * Which branches, tags and stashes include the commit. 
    * Filter the branches shown in Git Graph using the 'Branches' dropdown menu. The options for filtering the branches are:
        * Show All branches
        * Select one or more branches to be viewed
        * Select from a user predefined array of custom glob patterns (by setting `git-graph.customBranchGlobPatterns`)
    * Fetch from Remote(s) _(available on the top control bar)_
    * Find Widget allows you to quickly find one or more commits containing a specific phrase (in the commit message / date / author / hash, branch or tag names).
    * Repository Settings Widget:
        * Allows you to view, add, edit, delete, fetch & prune remotes of the repository.
        * Configure "Issue Linking" - Converts issue numbers in commit messages into hyperlinks, that open the issue in your issue tracking system.
        * Configure "Pull Request Creation" - Automates the opening and pre-filling of a Pull Request form, directly from a branches context menu.
            * Support for the publicly hosted Bitbucket, GitHub and GitLab Pull Request providers is built-in.
            * Custom Pull Request providers can be configured using the Extension Setting `git-graph.customPullRequestProviders` (e.g. for use with privately hosted Pull Request providers). Information on how to configure custom providers is available [here](https://github.com/hansu/vscode-git-graph/wiki/Configuring-a-custom-Pull-Request-Provider).
        * Export your Git Graph Repository Configuration to a file that can be committed in the repository. It allows others working in the same repository to automatically use the same Git Graph configuration.
    * Keyboard Shortcuts (available in the Git Graph View):
        * `CTRL/CMD + F`: Open the Find Widget.
        * `CTRL/CMD + H`: Scrolls the Git Graph View to be centered on the commit referenced by HEAD.
        * `CTRL/CMD + R`: Refresh the Git Graph View.
        * `CTRL/CMD + S`: Scrolls the Git Graph View to the first (or next) stash in the loaded commits.
        * `CTRL/CMD + SHIFT + S`: Scrolls the Git Graph View to the last (or previous) stash in the loaded commits.
        * When the Commit Details View is open on a commit:
            * `Up` / `Down`: The Commit Details View will be opened on the commit directly above or below it on the Git Graph View.
            * `CTRL/CMD + Up` / `CTRL/CMD + Down`: The Commit Details View will be opened on its child or parent commit on the same branch.
                * If the Shift Key is also pressed (i.e. `CTRL/CMD + SHIFT + Up` / `CTRL/CMD + SHIFT + Down`), when branches or merges are encountered the alternative branch is followed.
        * `Enter`: If a dialog is open, pressing enter submits the dialog, taking the primary (left) action.
        * `Escape`: Closes the active dialog, context menu or the Commit Details View.
    * Resize the width of each column, and show/hide the Date, Author & Commit columns.
    * Common Emoji Shortcodes are automatically replaced with the corresponding emoji in commit messages (including all [gitmoji](https://gitmoji.carloscuesta.me/)). Custom Emoji Shortcode mappings can be defined in `git-graph.customEmojiShortcodeMappings`.
* A broad range of configurable settings (e.g. graph style, branch colours, and more...). See the 'Extension Settings' section below for more information.
* "Git Graph" launch button in the Status Bar
* "Git Graph: View Git Graph" launch command in the Command Palette

## Extension Settings

Detailed information of all Git Graph settings is available [here](https://github.com/hansu/vscode-git-graph/wiki/Extension-Settings), including: descriptions, screenshots, default values and types (not up to date).

A summary of the Git Graph extension settings are:
* **Commit Details View**:
    * **Auto Center**: Automatically center the Commit Details View when it is opened.
    * **File View**:
        * **File Tree**:
            * **Compact Folders**: Render the File Tree in the Commit Details View in a compacted form, such that folders with a single child folder are compressed into a single combined folder element.
        * **Type**: Sets the default type of File View used in the Commit Details View.
    * **Location**: Specifies where the Commit Details View is rendered in the Git Graph View.

* **Initially Hide Summary**: Controls whether the commit summary is collapsed (hidden) or expanded when starting Git Graph.
* **Context Menu Actions Visibility**: Customise which context menu actions are visible. For more information, see the documentation [here](https://github.com/hansu/vscode-git-graph/wiki/Extension-Settings#context-menu-actions-visibility).
* **Custom Branch Glob Patterns**: An array of Custom Glob Patterns to be shown in the "Branches" dropdown. Example: `[{"name":"Feature Requests", "glob":"heads/feature/*"}]`
* **Custom Emoji Shortcode Mappings**: An array of custom Emoji Shortcode mappings. Example: `[{"shortcode": ":sparkles:", "emoji":"✨"}]`
* **Custom Pull Request Providers**: An array of custom Pull Request providers that can be used in the "Pull Request Creation" Integration. For information on how to configure this setting, see the documentation [here](https://github.com/hansu/vscode-git-graph/wiki/Configuring-a-custom-Pull-Request-Provider).
* **Date**:
    * **Format**: Specifies the date format to be used in the "Date" column on the Git Graph View.
    * **Type**: Specifies the date type to be displayed in the "Date" column on the Git Graph View, either the author or commit date.
* **Default Column Visibility**: An object specifying the default visibility of the Date, Author & Commit columns. Example: `{"Date": true, "Author": true, "Commit": true}`
* **Dialog > \***: Set the default options on the following dialogs: Add Tag, Apply Stash, Cherry Pick, Create Branch, Delete Branch, Fetch into Local Branch, Fetch Remote, Merge, Pop Stash, Pull Branch, Rebase, Reset, and Stash Uncommitted Changes
* **Enhanced Accessibility**: Visual file change A|M|D|R|U indicators in the Commit Details View for users with colour blindness. In the future, this setting will enable any additional accessibility related features of Git Graph that aren't enabled by default.
* **File Encoding**: The character set encoding used when retrieving a specific version of repository files (e.g. in the Diff View). A list of all supported encodings can be found [here](https://github.com/ashtuchkin/iconv-lite/wiki/Supported-Encodings).
* **Graph**:
    * **Colours**: Specifies the colours used on the graph.
    * **Style**: Specifies the style of the graph.
    * **Uncommitted Changes**: Specifies how the Uncommitted Changes are displayed on the graph.
* **Integrated Terminal Shell**: Specifies the path and filename of the Shell executable to be used by the Visual Studio Code Integrated Terminal, when it is opened by Git Graph.
* **Keyboard Shortcut > \***: Configures the keybindings used for all keyboard shortcuts in the Git Graph View.
* **Markdown**: Parse and render a frequently used subset of inline Markdown formatting rules in commit messages and tag details (bold, italics, bold & italics, and inline code blocks).
* **Max Depth Of Repo Search**: Specifies the maximum depth of subfolders to search when discovering repositories in the workspace.
* **Max Depth Of Repo Search**: Specifies the maximum depth of subfolders to search when discovering repositories in the workspace.
* **Open New Tab Editor Group**: Specifies the Editor Group where Git Graph should open new tabs, when performing the following actions from the Git Graph View: Viewing the Visual Studio Code Diff View, Opening a File, Viewing a File at a Specific Revision.
* **Open to the Repo of the Active Text Editor Document**: Open the Git Graph View to the repository containing the active Text Editor document.
* **Reference Labels**:
    * **Alignment**: Specifies how branch and tag reference labels are aligned for each commit.
    * **Combine Local and Remote Branch Labels**: Combine local and remote branch labels if they refer to the same branch, and are on the same commit.
* **Repository**:
    * **Commits**:
        * **Fetch Avatars**: Fetch avatars of commit authors and committers.
        * **Initial Load**: Specifies the number of commits to initially load.
        * **Load More**: Specifies the number of additional commits to load when the "Load More Commits" button is pressed, or more commits are automatically loaded.
        * **Load More Automatically**: When the view has been scrolled to the bottom, automatically load more commits if they exist (instead of having to press the "Load More Commits" button).
        * **Mute**:
            * **Commits that are not ancestors of HEAD**: Display commits that aren't ancestors of the checked-out branch / commit with a muted text color.
            * **Merge Commits**: Display merge commits with a muted text color.
        * **Order**: Specifies the order of commits on the Git Graph View. See [git log](https://git-scm.com/docs/git-log#_commit_ordering) for more information on each order option.
        * **Show Signature Status**: Show the commit's signature status to the right of the Committer in the Commit Details View (only for signed commits). Hovering over the signature icon displays a tooltip with the signature details.
    * **Fetch and Prune**: Before fetching from remote(s) using the Fetch button on the Git Graph View Control Bar, remove any remote-tracking references that no longer exist on the remote(s).
    * **Fetch And Prune Tags**: Before fetching from remote(s) using the Fetch button on the Git Graph View Control Bar, remove any local tags that no longer exist on the remote(s).
    * **Include Commits Mentioned By Reflogs**: Include commits only mentioned by reflogs in the Git Graph View (only applies when showing all branches).
    * **On Load**:
        * **Scroll To Head**: Automatically scroll the Git Graph View to be centered on the commit referenced by HEAD.
        * **Show Checked Out Branch**: Show the checked out branch when a repository is loaded in the Git Graph View.
        * **Show Specific Branches**: Show specific branches when a repository is loaded in the Git Graph View.
    * **Only Follow First Parent**: Only follow the first parent of commits when discovering the commits to load in the Git Graph View. See [--first-parent](https://git-scm.com/docs/git-log#Documentation/git-log.txt---first-parent) to find out more about this setting.
    * **Show Commits Only Referenced By Tags**: Show Commits that are only referenced by tags in Git Graph.
    * **Show Remote Branches**: Show Remote Branches in Git Graph by default.
    * **Show Remote Heads**: Show Remote HEAD Symbolic References in Git Graph.
    * **Show Stashes**: Show Stashes in Git Graph by default.
    * **Show Tags**: Show Tags in Git Graph by default.
    * **Show Uncommitted Changes**: Show uncommitted changes. If you work on large repositories, disabling this setting can reduce the load time of the Git Graph View.
    * **Show Untracked Files**: Show untracked files when viewing the uncommitted changes. If you work on large repositories, disabling this setting can reduce the load time of the Git Graph View.
    * **Sign**:
        * **Commits**: Enables commit signing with GPG or X.509.
        * **Tags**: Enables tag signing with GPG or X.509.
    * **Use Mailmap**: Respect [.mailmap](https://git-scm.com/docs/git-check-mailmap#_mapping_authors) files when displaying author & committer names and email addresses.
* **Repository Dropdown Order**: Specifies the order that repositories are sorted in the repository dropdown on the Git Graph View (only visible when more than one repository exists in the current Visual Studio Code Workspace).
* **Retain Context When Hidden**: Specifies if the Git Graph view Visual Studio Code context is kept when the panel is no longer visible (e.g. moved to background tab). Enabling this setting will make Git Graph load significantly faster when switching back to the Git Graph tab, however has a higher memory overhead.
* **Show Status Bar Item**: Show a Status Bar Item that opens the Git Graph View when clicked.
* **Source Code Provider Integration Location**: Specifies where the "View Git Graph" action appears on the title of SCM Providers.
* **Tab Icon Colour Theme**: Specifies the colour theme of the icon displayed on the Git Graph tab.
* **ToolbarButtonVisibility** : Configure the visibility of toolbar items. Currently supported: `{"Remotes": true, "Simplify": true}`

This extension consumes the following settings:

* `git.path`: Specifies the path and filename of a portable Git installation.

## Extension Commands

This extension contributes the following commands:

* `git-graph.view`: Git Graph: View Git Graph
* `git-graph.addGitRepository`: Git Graph: Add Git Repository... _(used to add sub-repos to Git Graph)_
* `git-graph.clearAvatarCache`: Git Graph: Clear Avatar Cache
* `git-graph.endAllWorkspaceCodeReviews`: Git Graph: End All Code Reviews in Workspace
* `git-graph.endSpecificWorkspaceCodeReview`: Git Graph: End a specific Code Review in Workspace... _(used to end a specific Code Review without having to first open it in the Git Graph View)_
* `git-graph.fetch`: Git Graph: Fetch from Remote(s) _(used to open the Git Graph View and immediately run "Fetch from Remote(s)")_
* `git-graph.removeGitRepository`: Git Graph: Remove Git Repository... _(used to remove repositories from Git Graph)_
* `git-graph.resumeWorkspaceCodeReview`: Git Graph: Resume a specific Code Review in Workspace... _(used to open the Git Graph View to a Code Review that is already in progress)_
* `git-graph.version`: Git Graph: Get Version Information

## Release Notes

Detailed Release Notes are available [here](CHANGELOG.md).

## Acknowledgements

Thank you to all of the contributors that help with the development of Git Graph!

Some of the icons used in Git Graph are from the following sources, please support them for their excellent work!
- [GitHub Octicons](https://octicons.github.com/) ([License](https://github.com/primer/octicons/blob/master/LICENSE))
- [Icons8](https://icons8.com/icon/pack/free-icons/ios11) ([License](https://icons8.com/license))

---

# Git Graph Erweiterung für Visual Studio Code (deutsch)

Fork von mhutchie's Git Graph mit weiteren Verbesserungen.
Hauptverbesserungen:

* Auswahl einzelner Branches und/oder Autoren. Aktivierbar mit `git-graph.repository.singleBranchSelect` und `git-graph.repository.singleAuthorSelect`
* Button zum Einklappen der Commit-Zusammenfassung hinzugefügt (hansu#3)
* Checkbox 'Unzusammenhängende Historien zulassen' bei Merge-Aktion hinzugefügt
* Neue Einstellung `git-graph.toolbarButtonVisibility` zur Konfiguration der Sichtbarkeit einiger Elemente der Toolbar. Zum Beispiel: `{"Remotes": true, "Simplify": true}`
* SimplifyByDecoration Checkbox hinzugefügt (hansu#33)
* Fehler behoben: Rechtsklick öffnet natives Kontextmenü unter macOS (hansu#38)
* Button zum Springen zu HEAD hinzugefügt (hansu#14)
* Einklappen/Ausklappen-Buttons zur Commit-Diff-Ansicht hinzugefügt (hansu#6)
* Spaltenbreite ohne Header ändern (hansu#4)
* Autorenfilter hinzugefügt (hansu#1)
* Option für Sticky Header hinzugefügt (mhutchie#132)

![Ergänzungen](https://github.com/hansu/vscode-git-graph/raw/master/resources/demo.gif)

## Installation

1. Lade die neueste Version von https://github.com/hansu/vscode-git-graph/releases herunter (lade die .vsix-Datei im Bereich "Assets" herunter).

2. Führe den VS-Code-Befehl "Erweiterungen: Aus VSIX installieren..." aus.

## Funktionen

* Git-Graph-Ansicht:
    * Anzeigen:
        * Lokale & Remote Branches
        * Lokale Referenzen: Heads, Tags & Remotes
        * Nicht committete Änderungen
    * Git-Aktionen ausführen (verfügbar per Rechtsklick auf einen Commit / Branch / Tag):
        * Branches erstellen, auschecken, löschen, fetchen, mergen, pullen, pushen, rebasen, umbenennen & zurücksetzen
        * Tags hinzufügen, löschen & pushen
        * Commits auschecken, Cherry-picken, verwerfen, mergen & zurücksetzen
        * Nicht committete Änderungen bereinigen, zurücksetzen & sichern (stash)
        * Stashes anwenden, Branches daraus erstellen, verwerfen & wiederherstellen (pop)
        * Details zu annotierten Tags anzeigen (Name, E-Mail, Datum und Nachricht)
        * Commit-Hashes und Branch-, Stash- & Tag-Namen in die Zwischenablage kopieren
    * Commit-Details und Dateiänderungen anzeigen, indem du auf einen Commit klickst. In der Commit-Details-Ansicht kannst du:
        * Die Visual Studio Code Diff-Ansicht jeder Dateiänderung anzeigen, indem du darauf klickst.
        * Die aktuelle Version jeder Datei öffnen, die im Commit geändert wurde.
        * Den Pfad jeder Datei, die im Commit geändert wurde, in die Zwischenablage kopieren.
        * Auf jede HTTP/HTTPS-URL im Commit-Body klicken, um sie im Standard-Webbrowser zu öffnen.
    * Zwei beliebige Commits vergleichen, indem du auf einen Commit klickst und dann bei gedrückter STRG/CMD-Taste auf einen anderen Commit klickst. In der Commit-Vergleichsansicht kannst du:
        * Die Visual Studio Code Diff-Ansicht jeder Dateiänderung zwischen den ausgewählten Commits anzeigen, indem du darauf klickst.
        * Die aktuelle Version jeder Datei öffnen, die zwischen den ausgewählten Commits geändert wurde.
        * Den Pfad jeder Datei, die zwischen den ausgewählten Commits geändert wurde, in die Zwischenablage kopieren.
    * Code Review - Behalte den Überblick darüber, welche Dateien du in den Commit-Detail- und Vergleichsansichten überprüft hast.
        * Code Reviews können für jeden Commit oder zwischen zwei beliebigen Commits durchgeführt werden (nicht für nicht committete Änderungen).
        * Wenn ein Code Review gestartet wird, werden alle zu überprüfenden Dateien fett dargestellt. Wenn du dir den Diff ansiehst oder eine Datei öffnest, wird sie nicht mehr fett dargestellt.
        * Code Reviews bleiben über Visual Studio Code-Sitzungen hinweg erhalten. Sie werden nach 90 Tagen Inaktivität automatisch geschlossen.
    * Nicht committete Änderungen anzeigen und die nicht committeten Änderungen mit jedem Commit vergleichen.
    * Bewege den Mauszeiger über einen beliebigen Commit-Vertex im Graphen, um einen Tooltip anzuzeigen, der Folgendes angibt:
        * Ob der Commit in HEAD enthalten ist.
        * Welche Branches, Tags und Stashes den Commit enthalten.
    * Filtere die in Git Graph angezeigten Branches über das Dropdown-Menü "Branches". Die Optionen zum Filtern der Branches sind:
        * Alle Branches anzeigen
        * Einen oder mehrere Branches auswählen, die angezeigt werden sollen
        * Aus einem benutzerdefinierten Array von benutzerdefinierten Glob-Mustern auswählen (durch Festlegen von `git-graph.customBranchGlobPatterns`)
    * Von Remote(s) fetchen _(verfügbar in der oberen Kontrollleiste)_
    * Mit dem Such-Widget kannst du schnell einen oder mehrere Commits finden, die einen bestimmten Ausdruck enthalten (in der Commit-Nachricht / Datum / Autor / Hash, Branch- oder Tag-Namen).
    * Repository-Einstellungen-Widget:
        * Ermöglicht das Anzeigen, Hinzufügen, Bearbeiten, Löschen, Fetchen und Prune von Remotes des Repositorys.
        * "Issue Linking" konfigurieren - Konvertiert Issue-Nummern in Commit-Nachrichten in Hyperlinks, die das Issue in deinem Issue-Tracking-System öffnen.
        * "Pull Request Creation" konfigurieren - Automatisiert das Öffnen und Vorausfüllen eines Pull-Request-Formulars direkt aus dem Kontextmenü eines Branches.
            * Unterstützung für die öffentlich gehosteten Bitbucket-, GitHub- und GitLab-Pull-Request-Anbieter ist integriert.
            * Benutzerdefinierte Pull-Request-Anbieter können mit der Erweiterungseinstellung `git-graph.customPullRequestProviders` konfiguriert werden (z. B. zur Verwendung mit privat gehosteten Pull-Request-Anbietern). Informationen zur Konfiguration benutzerdefinierter Anbieter findest du [hier](https://github.com/hansu/vscode-git-graph/wiki/Configuring-a-custom-Pull-Request-Provider).
        * Exportiere deine Git-Graph-Repository-Konfiguration in eine Datei, die im Repository committet werden kann. So können andere, die im selben Repository arbeiten, automatisch dieselbe Git-Graph-Konfiguration verwenden.
    * Tastaturkürzel (verfügbar in der Git-Graph-Ansicht):
        * `STRG/CMD + F`: Such-Widget öffnen.
        * `STRG/CMD + H`: Scrollt die Git-Graph-Ansicht so, dass der von HEAD referenzierte Commit zentriert ist.
        * `STRG/CMD + R`: Git-Graph-Ansicht aktualisieren.
        * `STRG/CMD + S`: Scrollt die Git-Graph-Ansicht zum ersten (oder nächsten) Stash in den geladenen Commits.
        * `STRG/CMD + SHIFT + S`: Scrollt die Git-Graph-Ansicht zum letzten (oder vorherigen) Stash in den geladenen Commits.
        * Wenn die Commit-Details-Ansicht für einen Commit geöffnet ist:
            * `Hoch` / `Runter`: Die Commit-Details-Ansicht wird für den direkt darüber oder darunter liegenden Commit in der Git-Graph-Ansicht geöffnet.
            * `STRG/CMD + Hoch` / `STRG/CMD + Runter`: Die Commit-Details-Ansicht wird für den Kind- oder Eltern-Commit auf demselben Branch geöffnet.
                * Wenn die Umschalttaste ebenfalls gedrückt wird (d. h. `STRG/CMD + SHIFT + Hoch` / `STRG/CMD + SHIFT + Runter`), wird beim Auftreten von Branches oder Merges der alternative Branch verfolgt.
        * `Enter`: Wenn ein Dialog geöffnet ist, wird durch Drücken der Eingabetaste der Dialog mit der primären (linken) Aktion bestätigt.
        * `Escape`: Schließt den aktiven Dialog, das Kontextmenü oder die Commit-Details-Ansicht.
    * Ändere die Breite jeder Spalte und blende die Spalten Datum, Autor und Commit ein/aus.
    * Gängige Emoji-Shortcodes werden in Commit-Nachrichten automatisch durch die entsprechenden Emojis ersetzt (einschließlich aller [gitmoji](https://gitmoji.carloscuesta.me/)). Benutzerdefinierte Emoji-Shortcode-Zuordnungen können in `git-graph.customEmojiShortcodeMappings` definiert werden.
* Eine breite Palette konfigurierbarer Einstellungen (z. B. Graph-Stil, Branch-Farben und mehr...). Weitere Informationen findest du im Abschnitt "Erweiterungseinstellungen" unten.
* "Git Graph"-Startbutton in der Statusleiste
* "Git Graph: Git-Graph anzeigen"-Startbefehl in der Befehlspalette

## Erweiterungseinstellungen

Detaillierte Informationen zu allen Git-Graph-Einstellungen findest du [hier](https://github.com/hansu/vscode-git-graph/wiki/Extension-Settings), einschließlich: Beschreibungen, Screenshots, Standardwerte und Typen (nicht aktuell).

Eine Zusammenfassung der Git-Graph-Erweiterungseinstellungen:
* **Commit-Details-Ansicht**:
    * **Automatisch zentrieren**: Zentriert die Commit-Details-Ansicht automatisch, wenn sie geöffnet wird.
    * **Dateiansicht**:
        * **Dateibaum**:
            * **Kompakte Ordner**: Rendert den Dateibaum in der Commit-Details-Ansicht in einer kompakten Form, sodass Ordner mit einem einzelnen Unterordner zu einem einzigen kombinierten Ordnerelement zusammengefasst werden.
        * **Typ**: Legt den Standardtyp der Dateiansicht fest, die in der Commit-Details-Ansicht verwendet wird.
    * **Position**: Gibt an, wo die Commit-Details-Ansicht in der Git-Graph-Ansicht gerendert wird.

* **Initial Zusammenfassung ausblenden**: Steuert, ob die Commit-Zusammenfassung beim Starten von Git Graph eingeklappt (ausgeblendet) oder erweitert ist.
* **Sichtbarkeit der Kontextmenüaktionen**: Anpassen, welche Kontextmenüaktionen sichtbar sind. Weitere Informationen findest du in der Dokumentation [hier](https://github.com/hansu/vscode-git-graph/wiki/Extension-Settings#context-menu-actions-visibility).
* **Benutzerdefinierte Branch-Glob-Muster**: Ein Array von benutzerdefinierten Glob-Mustern, die im Dropdown-Menü "Branches" angezeigt werden. Beispiel: `[{"name":"Feature Requests", "glob":"heads/feature/*"}]`
* **Benutzerdefinierte Emoji-Shortcode-Zuordnungen**: Ein Array von benutzerdefinierten Emoji-Shortcode-Zuordnungen. Beispiel: `[{"shortcode": ":sparkles:", "emoji":"✨"}]`
* **Benutzerdefinierte Pull-Request-Anbieter**: Ein Array von benutzerdefinierten Pull-Request-Anbietern, die in der Integration "Pull-Request-Erstellung" verwendet werden können. Informationen zur Konfiguration dieser Einstellung findest du in der Dokumentation [hier](https://github.com/hansu/vscode-git-graph/wiki/Configuring-a-custom-Pull-Request-Provider).
* **Datum**:
    * **Format**: Gibt das Datumsformat an, das in der Spalte "Datum" in der Git-Graph-Ansicht verwendet werden soll.
    * **Typ**: Gibt den Datentyp an, der in der Spalte "Datum" in der Git-Graph-Ansicht angezeigt werden soll, entweder das Autoren- oder das Commit-Datum.
* **Standardmäßige Spaltensichtbarkeit**: Ein Objekt, das die Standardsichtbarkeit der Spalten Datum, Autor und Commit angibt. Beispiel: `{"Date": true, "Author": true, "Commit": true}`
* **Dialog > \***: Legt die Standardoptionen für die folgenden Dialoge fest: Tag hinzufügen, Stash anwenden, Cherry-Pick, Branch erstellen, Branch löschen, In lokalen Branch fetchen, Remote fetchen, Mergen, Stash wiederherstellen, Branch pullen, Rebasen, Zurücksetzen und Nicht committete Änderungen sichern.
* **Verbesserte Barrierefreiheit**: Visuelle Dateiänderungsanzeigen A|M|D|R|U in der Commit-Details-Ansicht für Benutzer mit Farbenblindheit. In Zukunft wird diese Einstellung alle zusätzlichen barrierefreiheitsbezogenen Funktionen von Git Graph aktivieren, die nicht standardmäßig aktiviert sind.
* **Dateikodierung**: Die Zeichensatzkodierung, die beim Abrufen einer bestimmten Version von Repository-Dateien verwendet wird (z. B. in der Diff-Ansicht). Eine Liste aller unterstützten Kodierungen findest du [hier](https://github.com/ashtuchkin/iconv-lite/wiki/Supported-Encodings).
* **Graph**:
    * **Farben**: Gibt die im Graphen verwendeten Farben an.
    * **Stil**: Gibt den Stil des Graphen an.
    * **Nicht committete Änderungen**: Gibt an, wie die nicht committeten Änderungen im Graphen angezeigt werden.
* **Integrierte Terminal-Shell**: Gibt den Pfad und Dateinamen der Shell-Executable an, die vom integrierten Terminal von Visual Studio Code verwendet werden soll, wenn es von Git Graph geöffnet wird.
* **Tastaturkürzel > \***: Konfiguriert die Tastenkombinationen, die für alle Tastaturkürzel in der Git-Graph-Ansicht verwendet werden.
* **Markdown**: Analysiert und rendert eine häufig verwendete Teilmenge von Inline-Markdown-Formatierungsregeln in Commit-Nachrichten und Tag-Details (fett, kursiv, fett & kursiv und Inline-Codeblöcke).
* **Maximale Suchtiefe im Repository**: Gibt die maximale Tiefe der zu durchsuchenden Unterordner beim Entdecken von Repositorys im Arbeitsbereich an.
* **Öffnen neuer Tab-Editor-Gruppe**: Gibt die Editor-Gruppe an, in der Git Graph neue Tabs öffnen soll, wenn die folgenden Aktionen in der Git-Graph-Ansicht ausgeführt werden: Anzeigen der Visual Studio Code Diff-Ansicht, Öffnen einer Datei, Anzeigen einer Datei in einer bestimmten Revision.
* **Zum Repository des aktiven Text-Editor-Dokuments öffnen**: Öffnet die Git-Graph-Ansicht für das Repository, das das aktive Text-Editor-Dokument enthält.
* **Referenzbezeichnungen**:
    * **Ausrichtung**: Gibt an, wie Branch- und Tag-Referenzbezeichnungen für jeden Commit ausgerichtet werden.
    * **Lokale und Remote-Branch-Bezeichnungen kombinieren**: Kombiniert lokale und Remote-Branch-Bezeichnungen, wenn sie sich auf denselben Branch beziehen und sich auf demselben Commit befinden.
* **Repository**:
    * **Commits**:
        * **Avatare abrufen**: Ruft Avatare von Commit-Autoren und -Committern ab.
        * **Initial laden**: Gibt die Anzahl der anfänglich zu ladenden Commits an.
        * **Mehr laden**: Gibt die Anzahl der zusätzlichen Commits an, die geladen werden sollen, wenn die Schaltfläche "Mehr Commits laden" gedrückt wird oder weitere Commits automatisch geladen werden.
        * **Automatisch mehr laden**: Wenn die Ansicht nach unten gescrollt wurde, werden automatisch weitere Commits geladen, sofern vorhanden (anstatt die Schaltfläche "Mehr Commits laden" drücken zu müssen).
        * **Stummschalten**:
            * **Commits, die keine Vorgänger von HEAD sind**: Zeigt Commits, die keine Vorgänger des ausgecheckten Branches / Commits sind, mit einer stummgeschalteten Textfarbe an.
            * **Merge-Commits**: Zeigt Merge-Commits mit einer stummgeschalteten Textfarbe an.
        * **Reihenfolge**: Gibt die Reihenfolge der Commits in der Git-Graph-Ansicht an. Weitere Informationen zu den einzelnen Sortieroptionen findest du unter [git log](https://git-scm.com/docs/git-log#_commit_ordering).
        * **Signaturstatus anzeigen**: Zeigt den Signaturstatus des Commits rechts neben dem Committer in der Commit-Details-Ansicht an (nur für signierte Commits). Wenn Sie den Mauszeiger über das Signatursymbol bewegen, wird ein Tooltip mit den Signaturdetails angezeigt.
    * **Fetch and Prune**: Bevor von Remotes mit der Schaltfläche "Fetch" in der Git-Graph-Steuerleiste geholt wird, entferne alle Remote-Tracking-Referenzen, die nicht mehr auf den Remotes vorhanden sind.
    * **Fetch and Prune Tags**: Bevor von Remotes mit der Schaltfläche "Fetch" in der Git-Graph-Steuerleiste geholt wird, entferne alle lokalen Tags, die nicht mehr auf den Remotes vorhanden sind.
    * **Commits einschließen, die von Reflogs erwähnt werden**: Schließt Commits ein, die nur von Reflogs in der Git-Graph-Ansicht erwähnt werden (gilt nur, wenn alle Branches angezeigt werden).
    * **Beim Laden**:
        * **Zu HEAD scrollen**: Scrollt die Git-Graph-Ansicht automatisch so, dass der von HEAD referenzierte Commit zentriert ist.
        * **Ausgecheckten Branch anzeigen**: Zeigt den ausgecheckten Branch an, wenn ein Repository in der Git-Graph-Ansicht geladen wird.
        * **Bestimmte Branches anzeigen**: Zeigt bestimmte Branches an, wenn ein Repository in der Git-Graph-Ansicht geladen wird.
    * **Nur dem ersten Elternteil folgen**: Folgt nur dem ersten Elternteil von Commits, wenn die zu ladenden Commits in der Git-Graph-Ansicht ermittelt werden. Weitere Informationen zu dieser Einstellung findest du unter [--first-parent](https://git-scm.com/docs/git-log#Documentation/git-log.txt---first-parent).
    * **Nur Commits anzeigen, auf die von Tags verwiesen wird**: Zeigt Commits an, auf die nur von Tags in Git Graph verwiesen wird.
    * **Remote Branches anzeigen**: Zeigt standardmäßig Remote Branches in Git Graph an.
    * **Remote HEADs anzeigen**: Zeigt symbolische Remote-HEAD-Referenzen in Git Graph an.
    * **Stashes anzeigen**: Zeigt standardmäßig Stashes in Git Graph an.
    * **Tags anzeigen**: Zeigt standardmäßig Tags in Git Graph an.
    * **Nicht committete Änderungen anzeigen**: Zeigt nicht committete Änderungen an. Wenn du mit großen Repositorys arbeitest, kann das Deaktivieren dieser Einstellung die Ladezeit der Git-Graph-Ansicht verkürzen.
    * **Nicht verfolgte Dateien anzeigen**: Zeigt nicht verfolgte Dateien an, wenn die nicht committeten Änderungen angezeigt werden. Wenn du mit großen Repositorys arbeitest, kann das Deaktivieren dieser Einstellung die Ladezeit der Git-Graph-Ansicht verkürzen.
    * **Signieren**:
        * **Commits**: Aktiviert das Signieren von Commits mit GPG oder X.509.
        * **Tags**: Aktiviert das Signieren von Tags mit GPG oder X.509.
    * **Mailmap verwenden**: Berücksichtigt [.mailmap](https://git-scm.com/docs/git-check-mailmap#_mapping_authors)-Dateien bei der Anzeige von Namen und E-Mail-Adressen von Autoren und Committern.
* **Reihenfolge der Repository-Dropdown-Liste**: Gibt die Reihenfolge an, in der Repositorys in der Repository-Dropdown-Liste in der Git-Graph-Ansicht sortiert werden (nur sichtbar, wenn im aktuellen Visual Studio Code-Arbeitsbereich mehrere Repositorys vorhanden sind).
* **Kontext beibehalten, wenn ausgeblendet**: Gibt an, ob der Visual Studio Code-Kontext der Git-Graph-Ansicht beibehalten wird, wenn der Bereich nicht mehr sichtbar ist (z. B. in den Hintergrund-Tab verschoben). Wenn diese Einstellung aktiviert ist, wird Git Graph beim Zurückwechseln zum Git-Graph-Tab deutlich schneller geladen, hat jedoch einen höheren Speicherbedarf.
* **Statusleistenelement anzeigen**: Zeigt ein Statusleistenelement an, das beim Klicken die Git-Graph-Ansicht öffnet.
* **Position der Integration des Quellcode-Anbieters**: Gibt an, wo die Aktion "Git-Graph anzeigen" im Titel von SCM-Anbietern angezeigt wird.
* **Farbthema des Tab-Symbols**: Gibt das Farbthema des auf dem Git-Graph-Tab angezeigten Symbols an.
* **ToolbarButtonVisibility**: Konfiguriert die Sichtbarkeit von Toolbar-Elementen. Derzeit unterstützt: `{"Remotes": true, "Simplify": true}`

Diese Erweiterung verwendet die folgenden Einstellungen:

* `git.path`: Gibt den Pfad und Dateinamen einer portablen Git-Installation an.

## Erweiterungsbefehle

Diese Erweiterung stellt die folgenden Befehle bereit:

* `git-graph.view`: Git-Graph: Git-Graph anzeigen
* `git-graph.addGitRepository`: Git-Graph: Git-Repository hinzufügen... _(zum Hinzufügen von Sub-Repos zu Git Graph)_
* `git-graph.clearAvatarCache`: Git-Graph: Avatar-Cache löschen
* `git-graph.endAllWorkspaceCodeReviews`: Git-Graph: Alle Code-Reviews im Arbeitsbereich beenden
* `git-graph.endSpecificWorkspaceCodeReview`: Git-Graph: Ein bestimmtes Code-Review im Arbeitsbereich beenden... _(zum Beenden eines bestimmten Code-Reviews, ohne es zuerst in der Git-Graph-Ansicht öffnen zu müssen)_
* `git-graph.fetch`: Git-Graph: Von Remote(s) fetchen _(zum Öffnen der Git-Graph-Ansicht und sofortigen Ausführen von "Von Remote(s) fetchen")_
* `git-graph.removeGitRepository`: Git-Graph: Git-Repository entfernen... _(zum Entfernen von Repositorys aus Git Graph)_
* `git-graph.resumeWorkspaceCodeReview`: Git-Graph: Ein bestimmtes Code-Review im Arbeitsbereich fortsetzen... _(zum Öffnen der Git-Graph-Ansicht für ein bereits laufendes Code-Review)_
* `git-graph.version`: Git-Graph: Versionsinformationen abrufen

## Versionshinweise

Detaillierte Versionshinweise sind [hier](CHANGELOG.md) verfügbar.

## Danksagungen

Vielen Dank an alle Mitwirkenden, die bei der Entwicklung von Git Graph helfen!

Einige der in Git Graph verwendeten Icons stammen aus den folgenden Quellen. Bitte unterstützt sie für ihre hervorragende Arbeit!
- [GitHub Octicons](https://octicons.github.com/) ([Lizenz](https://github.com/primer/octicons/blob/master/LICENSE))
- [Icons8](https://icons8.com/icon/pack/free-icons/ios11) ([Lizenz](https://icons8.com/license))