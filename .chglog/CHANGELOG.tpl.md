{{ if .Versions }}
# Changelog

{{ range .Versions }}
## [{{ .Tag }}] - {{ .Date }}

{{ if .Changes }}
### Changed
{{ range .Changes }}
- {{ .Header }}
  {{ end }}
  {{ end }}

{{ end }}
{{ end }}
