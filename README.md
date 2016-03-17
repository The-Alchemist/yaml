# YAML

![](https://travis-ci.org/owainlewis/yaml.svg?branch=master)

An updated YAML library for Clojure based on Snake YAML and heavily inspired by clj-yaml

## Install

### Lein

[![Clojars Project](http://clojars.org/io.forward/yaml/latest-version.svg)](http://clojars.org/io.forward/yaml)

## Usage

```clojure
(ns demo.core
  (:refer-clojure :exclude [load])
  (:require [yaml.core :as yaml]))

;; Note on DSL
;; yaml/load & yaml/parse-string are identical
;; yaml/dump & yaml/generate-string are identical

;; Parse a YAML file

(yaml/from-file "config.yml")

;; Parse a YAML string

(yaml/parse-string "foo: bar")

;; Dump YAML

(yaml/generate-string {:foo "bar"})

;; Examples

(yaml/generate-string [{:name "John Smith", :age 33} {:name "Mary Smith", :age 27}])
;; "- {name: John Smith, age: 33}\n- {name: Mary Smith, age: 27}\n"

(yaml/parse-string "
- {name: John Smith, age: 33}
- name: Mary Smith
  age: 27
")

=> ({:name "John Smith", :age 33}
    {:name "Mary Smith", :age 27})
```

This is mainly an updated version of clj-yaml with some updates

1. Updates snake YAML to latest version
2. Split reader and writer into separate protocols and files
3. Ability to read YAML from file in single function
4. Return vector [] instead of list when parsing java.util.ArrayList

## License

Copyright © 2016 Owain Lewis

Distributed under the Eclipse Public License
