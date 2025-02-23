{{ if .Versions }}
# Changelog

{{ range .Versions }}
## [{{ .Tag }}] - {{ datetime "2006-01-02 16:25" .Tag.Date }}

{{ if .Commits }}
### Changed
{{ range .Commits }}
- {{ if .Scope }}**{{ .Scope }}:** {{ end }}{{ .Subject }}
  {{ if .TrimmedBody -}}
  {{ indent .TrimmedBody 2 }}
  {{ end -}}
  {{ end }}

{{ end }}
{{ end }}
{{ end }}
