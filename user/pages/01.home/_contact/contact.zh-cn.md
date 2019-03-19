---
title: 联络
heading: 我们很希望听到您们的声音。
form:
    action: /home
    name: contact-form
    fields:
        -
            name: name
            label: 名称
            placeholder: 名称
            type: text
            validate:
                required: true
        -
            name: email
            label: 电子邮件
            placeholder: 电子邮件
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

如对网页有任何问题或意见，请随时联络我们。
