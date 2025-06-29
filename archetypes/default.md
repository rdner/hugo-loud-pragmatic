---
title: "{{ replace .Name "-" " " | strings.Title }}"
date: {{ .Date }}
description: ""
keywords: []
draft: true
params:
  author:
    name: "{{- .Site.Params.Author.Name -}}"
---
