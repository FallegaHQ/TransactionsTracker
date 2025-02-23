{{ if .Versions }}
{{ range .Versions }}
## [{{ .Tag.Name }}] - {{ datetime "2006-01-02" .Tag.Date }}

{{ if .Commits }}
### Changed
{{ range .Commits }}
- {{ if .Scope }}**{{ .Scope }}:** {{ end }}{{ .Subject }}
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
