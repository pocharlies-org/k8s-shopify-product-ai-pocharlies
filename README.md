# k8s-shopify-product-ai-pocharlies

Disabled k8s skeleton for `sauvage:/home/ubuntu/skirmshop/shopify-product-ai-app`.

The legacy edge route points `skirmshop.e-dani.com/product-ai` at host port
3459, but that port was not listening during the audit. This skeleton has no
IngressRoute and keeps the Deployment at `replicas: 0`.
