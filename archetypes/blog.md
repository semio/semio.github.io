+++
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
date = "{{ .Date }}"
url = '/blog/{{ dateFormat "2006/01/02" .Date }}/{{ .File.ContentBaseName }}/'
tags = []
categories = ["修"]
type = "blog"
draft = true
+++


