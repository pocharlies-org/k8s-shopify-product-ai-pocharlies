# ARCHITECTURE — k8s-shopify-product-ai-pocharlies

Esqueleto de despliegue **deshabilitado** para `shopify-product-ai-app`, que antes corría en `sauvage:/home/ubuntu/skirmshop/shopify-product-ai-app`.

## Clientes y versiones
- Ninguno activo: Deployment con `replicas: 0`, sin IngressRoute (la ruta legacy `skirmshop.e-dani.com/product-ai` apuntaba al puerto 3459 y no escuchaba). Tronco real: `main`; no hay Application de ArgoCD que lo cite (medido).

## Dependencias (ambos sentidos)
- Imagen prevista `harbor.e-dani.com/homelab/shopify-product-ai-app`; `externalsecret.yaml`. Sin repo fuente conocido. Nada lo consume.

## Stack
Kustomize + `manifest.yaml` plano.

## Componentes compartidos
Ninguno.

## Cómo se construye
`k8s/manifest.yaml`, `k8s/externalsecret.yaml`, `k8s/kustomization.yaml`; puerto 3459, `SHOPIFY_APP_URL=https://skirmshop.e-dani.com/product-ai`.

## Tests y validaciones
`reusable-ci.yml` (kustomize/kubeconform).

## CI/CD y despliegue
`ci.yml`. No se despliega: sin Application. Si se reactiva: crear la Application (repo GitOps), el IngressRoute y apuntar la fuente.

## Decisiones y trampas
- Candidato a archivar (ver nota de duplicados/abandonos del plan SC-1428). La función de «producto con IA» hoy la cubren `shopify-product-creator` y `k8s-shopify-admin-mcp`.
