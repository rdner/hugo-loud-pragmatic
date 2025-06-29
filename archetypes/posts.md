---
title: "{{ replace .Name "-" " " | strings.Title }}"
date: {{ .Date }}
description: ""
keywords: []
draft: true
params:
  tocEnabled: true
  coverCredit: ""
  author:
    pictureURL: "{{- .Site.Params.Author.PictureURL -}}"
    name: "{{- .Site.Params.Author.Name -}}"
    email: "{{- .Site.Params.Author.Email -}}"
---
