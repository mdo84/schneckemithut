---
title: yaml validation
author: markus
type: post
date: 2014-11-06T09:11:25+00:00
url: /?p=455
categories:
  - Allgemein

---
Um von der Command-Line seine Yaml-Files im Griff zu behalten, empfiehlt sich ruby:
  
`ruby -e "require 'yaml'; YAML.load_file('${YAML_PATH}')"`

Das ganze lässt sich in ein Shell-Script packen und nach /usr/bin legen:
  
`#!/bin/bash<br />
# yamlcheck in /usr/bin<br />
ruby -e "require 'yaml'; YAML.load_file('$1')"`

Der Aufruf erfolgt dann mit
  
`# yamlcheck <insert_yaml-file_here>`

Quelle:
  
http://blog.diabol.se/?p=576