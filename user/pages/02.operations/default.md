---
title: Operations
body_classes: header-transparent title-center
container_class: hkb-sm-container
onpage_menu: true
content:
    items: '@self.children'
access:
    site:
        login: true
login:
    visibility_requires_access: true
process:
    twig: true
cache_enable: false
---
# Welcome [color=red]{{ grav.user.fullname }}[/color].

Click on   
[`Operations->Edit Pages`](/operations/editpages) to edit  
or  
[`Operations->Review`](/operations/review) to check what has been done.
