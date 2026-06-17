# Payments API

## Descripción

`payments-api` es el servicio de procesamiento de pagos de **FinTech Peru**. Permite iniciar pagos, consultar su estado y anular operaciones pendientes.

Pertenece al sistema **banca-digital**, junto con los servicios de cuentas y operaciones transaccionales del dominio de banca.

## Equipo responsable

| | |
|---|---|
| **Grupo** | `banca-digital-team` |
| **Canal de contacto** | `#banca-digital` en Slack |

## Endpoints

| Método | Path | Descripción |
|--------|------|-------------|
| `POST` | `/payments` | Iniciar un pago |
| `GET` | `/payments/{id}` | Consultar estado de un pago |
| `DELETE` | `/payments/{id}` | Anular un pago pendiente |
| `GET` | `/health` | Health check |

## Ejemplo de uso

```bash
curl -X POST https://api.fintechperu.com/payments \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{
    "amount": 150.00,
    "currency": "PEN",
    "sourceAccountId": "acc-001",
    "destinationAccountId": "acc-002"
  }'
```

## Dependencias

Este servicio consume **`accounts-api`** para validar el origen de fondos antes de procesar un pago.
