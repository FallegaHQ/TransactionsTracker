{{ if .Versions }}
# Changelog

{{ range .Versions }}
## [{{ .Tag }}] - {{ datetime "2006-01-02 16:25" .Tag.Date }}

{{ if .Changes }}
### Changed
{{ range .Changes }}
- {{ .Header }}
  {{ end }}
  {{ end }}

{{ end }}
{{ end }}
