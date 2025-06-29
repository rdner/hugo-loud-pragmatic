---
title: "{{ replace .Name "-" " " | strings.Title }}"
date: {{ .Date }}
description: ""
keywords: []
draft: true
params:
  artist: "{{- .Site.Params.Author.Name -}}"
  author:
    name: "{{- .Site.Params.Author.Name -}}"
---
