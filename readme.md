# VSCode Settings

### Extensions

1. JetBrains Icons Theme
2. Bearded Theme
3. Fluent Icons
4. Live Server (Five server)
5. Prettier - Code formatter

### Config

```json
{
	// Window settings
	"window.openFilesInNewWindow": "off",
	"window.commandCenter": false,
	"window.zoomLevel": 1,
	"workbench.startupEditor": "none",
	"window.menuBarVisibility": "toggle",
	"workbench.activityBar.location": "top",

	// Editor settings
	"editor.tabSize": 2,
	"editor.folding": false,
	"editor.insertSpaces": false,
	"editor.smoothScrolling": true,
	"editor.minimap.enabled": false,
	"editor.detectIndentation": true,
	"editor.scrollBeyondLastLine": true,
	"editor.multiCursorModifier": "ctrlCmd",
	"editor.unicodeHighlight.ambiguousCharacters": false,
	"editor.cursorBlinking": "expand",
	"editor.glyphMargin": false,
	"editor.fontSize": 18,
	"editor.fontLigatures": true,
	"editor.fontFamily": "JetBrains Mono, monospace",
	"editor.defaultFormatter": "esbenp.prettier-vscode",
	"editor.renderControlCharacters": false,
	"editor.bracketPairColorization.enabled": false,
	"editor.lineHeight": 25,
	"files.exclude": {
		"**/.git": true,
		"**/.svn": true,
		"**/.hg": true,
		"**/CVS": true,
		"**/.DS_Store": true,
		"**/Thumbs.db": true,
		"**/node_modules": true
	},

	//Terminal
	"terminal.integrated.fontFamily": "FiraCode Nerd Font Mono",
	"terminal.integrated.fontSize": 15,
	"terminal.integrated.tabs.enabled": false,

	// Security
	"security.workspace.trust.untrustedFiles": "open",

	// CodeFormat
	"[html]": {
		"editor.defaultFormatter": "vscode.html-language-features"
	},
	"[json]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[jsonc]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[javascript]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[javascriptreact]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[typescript]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[typescriptreact]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[scss]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[css]": {
		"editor.defaultFormatter": "vscode.css-language-features"
	},

	//JS & TS
	"javascript.suggestionActions.enabled": false,
	"typescript.suggestionActions.enabled": false,
	"javascript.updateImportsOnFileMove.enabled": "always",
	"typescript.updateImportsOnFileMove.enabled": "always",

	// Breadcrumbs
	"breadcrumbs.enabled": false,

	// Explorer
	"explorer.confirmDelete": false,
	"explorer.compactFolders": false,
	"explorer.confirmDragAndDrop": false,

	// Workbench
	"workbench.editor.tabSizing": "shrink",
	"workbench.layoutControl.enabled": false,
	"workbench.settings.editor": "json",
	"workbench.iconTheme": "vscode-jetbrains-icon-theme-2023-dark",
	"workbench.productIconTheme": "fluent-icons",
	"workbench.list.smoothScrolling": true,

	// Debug
	"debug.toolBarLocation": "hidden",
	"debug.focusWindowOnBreak": false,
	"debug.showInlineBreakpointCandidates": false,
	"debug.showBreakpointsInOverviewRuler": false,
	"debug.allowBreakpointsEverywhere": false,
	"debug.autoExpandLazyVariables": false,
	"debug.confirmOnExit": "never",
	"debug.console.acceptSuggestionOnEnter": "off",
	"debug.console.closeOnEnd": false,
	"debug.console.collapseIdenticalLines": false,
	"debug.console.historySuggestions": false,
	"debug.disassemblyView.showSourceCode": false,
	"debug.enableStatusBarColor": false,
	"debug.focusEditorOnBreak": false,
	"debug.inlineValues": "off",
	"debug.internalConsoleOptions": "neverOpen",
	"debug.openDebug": "neverOpen",
	"debug.saveBeforeStart": "none",
	"debug.showInStatusBar": "never",
	"debug.openExplorerOnEnd": false,
	"debug.showSubSessionsInToolBar": false,
	"debug.terminal.clearBeforeReusing": false,

	// ========== Extensions settings ==========>

	// Prettier
	"prettier.semi": false,
	"prettier.useTabs": true,
	"editor.formatOnSave": true,
	"editor.formatOnPaste": true,
	"prettier.singleQuote": true,
	"prettier.jsxSingleQuote": true,
	"prettier.arrowParens": "avoid",
	"workbench.colorTheme": "Bearded Theme feat. Will"
}
```

# Powershell

> First you need to install all fonts (**_JetBrains Mono, FiraCode NerdFont Mono_**)

### ↓ user_profile.ps1 ↓

```powershell
# Prompt
Import-Module Terminal-Icons

# Load oh-my-posh config
function Get-ScriptDirectory { Split-Path $MyInvocation.ScriptName }
$PROMPT_CONFIG = Join-Path (Get-ScriptDirectory) 'withglasses.omp.json'
oh-my-posh --init --shell pwsh --config $PROMPT_CONFIG | Invoke-Expression

# PSReadLine options
# Set-PSReadlineOption -EditMode Emacs
# Set-PSReadLineOption -BellStyle None
# Set-PSReadLineKeyHandler -Chord 'Ctrl+d' -Function DeleteChar
# Set-PSReadLineOption -PredictionSource History
# Set-PSReadLineOption -PredictionViewStyle ListView

# Utilities
function which ($command) {
	Get-Command -Name $command -ErrorAction SilentlyContinue |
		Select-Object -ExpandProperty Path -ErrorAction SilentlyContinue
}

# Alias
Set-Alias ll ls
Set-Alias g git
Set-Alias vim nvim
```

---

**Set user_profile.ps1 as default config file**

### Open default config file

```bash
nvim $PROFILE.CurrentUserCurrentHost
```

### Write our config file path

```powershell
. $env:USERPROFILE\.config\powershell\user_profile.ps1
```

### ↓ withglasses.omp.json ↓

```json
{
	"$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json",
	"blocks": [
		{
			"alignment": "left",
			"segments": [
				{
					"background": "#29315A",
					"foreground": "#3EC669",
					"leading_diamond": "\ue0b6",
					"properties": {
						"style": "mixed"
					},
					"style": "diamond",
					"template": "\ue5ff {{ .Path }}",
					"trailing_diamond": "\ue0b4",
					"type": "path"
				},
				{
					"background": "#29315A",
					"foreground": "#43CCEA",
					"foreground_templates": [
						"{{ if or (.Working.Changed) (.Staging.Changed) }}#FF9248{{ end }}",
						"{{ if and (gt .Ahead 0) (gt .Behind 0) }}#ff4500{{ end }}",
						"{{ if gt .Ahead 0 }}#B388FF{{ end }}",
						"{{ if gt .Behind 0 }}#B388FF{{ end }}"
					],
					"leading_diamond": " \ue0b6",
					"properties": {
						"branch_max_length": 25,
						"fetch_stash_count": true,
						"fetch_status": true,
						"fetch_upstream_icon": true
					},
					"style": "diamond",
					"template": " {{ .UpstreamIcon }}{{ .HEAD }}{{if .BranchStatus }} {{ .BranchStatus }}{{ end }}{{ if .Working.Changed }} \uf044 {{ .Working.String }}{{ end }}{{ if and (.Working.Changed) (.Staging.Changed) }} |{{ end }}{{ if .Staging.Changed }} \uf046 {{ .Staging.String }}{{ end }}{{ if gt .StashCount 0 }} \uf692 {{ .StashCount }}{{ end }} ",
					"trailing_diamond": "\ue0b4",
					"type": "git"
				},

				{
					"foreground": "#C94A16",
					"style": "plain",
					"template": "x ",
					"type": "exit"
				}
			],
			"type": "prompt"
		},
		{
			"alignment": "right",
			"segments": [
				{
					"foreground": "#5fb157",
					"properties": {
						"display_mode": "files",
						"fetch_package_manager": true,
						"fetch_version": true,
						"npm_icon": "<#FE4A49>\ue71e npm</> ",
						"yarn_icon": "<#44FFD2>\uf487 yarn</> "
					},
					"style": "plain",
					"template": "{{ if .PackageManagerIcon }}{{ .PackageManagerIcon }} {{ end }}\ue718 {{ .Full }}",
					"type": "node"
				},
				{
					"foreground": "#4063D8",
					"properties": {
						"display_mode": "files",
						"fetch_version": true
					},
					"style": "plain",
					"template": " {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }}",
					"type": "crystal"
				},
				{
					"foreground": "#DE3F24",
					"properties": {
						"display_mode": "files",
						"fetch_version": true
					},
					"style": "plain",
					"template": " {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }}",
					"type": "ruby"
				},
				{
					"foreground": "#FED142",
					"properties": {
						"display_mode": "context",
						"fetch_virtual_env": false
					},
					"style": "plain",
					"template": " {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }}",
					"type": "python"
				}
			],
			"type": "prompt"
		},
		{
			"alignment": "left",
			"newline": true,
			"segments": [
				{
					"foreground": "#63F08C",
					"style": "plain",
					"template": "\u279c ",
					"type": "text"
				}
			],
			"type": "prompt"
		}
	],
	"version": 2
}
```

# Other

### Fonts

1. [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)
2. [Fira Code NerdFont Mono](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/FiraCode.zip)
