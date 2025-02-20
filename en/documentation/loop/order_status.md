---
layout: loop
title: Order status Loop
description: Order status loop displays order status information.
sidebar: loop
lang: en
subnav: loop_order_status
uses_global_argument: true
returns_global_outputs: { countable : true, timestampable : true, versionable : false }
type: order_status
arguments :
    - {name: "id", description: "A single or a list of order status ids.", example: "id=\"2\", id=\"1,4,7\""}

outputs :
    - {name: "$ID", description: "the order status id"}
    - {name: "$IS_TRANSLATED", description: "whatever the order status is translated or not"}
    - {name: "$CODE", description: "the order status code"}
    - {name: "$TITLE", description: "the order status title"}
    - {name: "$CHAPO", description: "the order status short description"}
    - {name: "$DESCRIPTION", description: "the order status description"}
    - {name: "$POSTSCRIPTUM", description: "the order status postscriptum"}
    - {name: "$LOCALE", description: "the order status locale"}
---