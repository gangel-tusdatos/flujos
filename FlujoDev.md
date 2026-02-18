🔁 Flujo de Desarrollo

```mermaid
flowchart LR
    A[Dev crea/actualiza feature branch] --> B[PR a develop]
    B --> C{CI/CD en develop: tests, linters, buenas prácticas}
    C -->|Falla| A
    C -->|OK| D[Dev aprueba y mergea a develop (sin TL)]
    D --> E[PR de develop a stage]
    E --> F{CI/CD en stage: tests, linters, buenas prácticas}
    F -->|Falla| A
    F -->|OK| G[Aprobación de TL]
    G --> H[Despliegue en ambiente stage]
    H --> I{QA y PO ejecutan QA funcional y E2E}
    I -->|Rechazado| A
    I -->|OK| J[PR de stage a prod]
    J --> K{CI/CD en prod: tests, linters, buenas prácticas}
    K -->|Falla| A
    K -->|OK| L{Aprobaciones requeridas: QA + PO + TL}
    L -->|Rechazado| A
    L -->|Aprobado| M[Despliegue a producción]
```
