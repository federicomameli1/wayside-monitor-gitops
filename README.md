# wayside-monitor-gitops

Argo CD values per gli ambienti del repo [`wayside-monitor`](https://github.com/federicomameli1/wayside-monitor).

## Struttura

- `environments/test/values.yaml` — aggiornato dal job `deploy-test` (merge in `main`).
- `environments/prod/values.yaml` — aggiornato dal job `deploy-prod` (release published).
- `environments/dev/pr-<N>/values.yaml` — creato/cancellato dai workflow `pr-dev` e `pr-cleanup`. **Non committare a mano qui dentro.**

## Convenzioni

- Le porte NodePort sono fisse: `30081` per test, `30082` per prod.
- Il `tag` dell'immagine viene riscritto dal CI a ogni promozione. Il `latest` iniziale viene sostituito al primo deploy reale.
- Prod gira con `replicaCount: 2`.
