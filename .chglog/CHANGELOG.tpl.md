{{ if .Versions }}
# Changelog

{{ range .Versions }}
## [{{ .Tag.Name }}] - {{ datetime "2006-01-02 16:25" .Tag.Date }}

{{ if .Commits }}
### Changed
{{ range .Commits }}
- {{ if .Scope }}**{{ .Scope }}:** {{ end }}{{ if .Icon }}{{ .Icon }} {{ end }}{{ .Subject }}
  {{ if .TrimmedBody -}}
  {{ indent .TrimmedBody 2 }}
  {{ end -}}
  {{ end }}

{{ else }}
- No changes
  {{ end }}

{{ end }}

{{ else }}
No versions found.
{{ end }}
