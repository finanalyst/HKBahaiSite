---
title: 歡迎
content:
    items: '@self.modular'
    order:
        by: default
        dir: asc
        custom:
            - _landing
            - _centenary
            - _belief
            - _unity
            - _words
            - _location
            - _contact
form:
    action: /home
    name: contact-form
    fields:
        -
            name: name
            label: 名稱
            placeholder: 名稱
            type: text
            validate:
                required: true
        -
            name: email
            label: 電子郵件
            placeholder: 電子郵件
            type: email
            validate:
                required: true
        -
            name: message
            label: 信息
            placeholder: 信息
            type: textarea
            rows: 6
            validate:
                required: true
    buttons:
        -
            type: submit
            value: '寄出信息'
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to: ['{{ config.plugins.email.from }}']
                subject: '[Contact] Message from {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: contact-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            display: thank-you
---
