# Contexto del sistema 
El modelo de datos representa un sistema completo para la gestión de aerolíneas.

# Propósito del modelo de datos
El modelo de datos tiene como objetivo estructurar la información necesaria para soportar los procesos operativos, comerciales y administrativos de una aerolínea. Permite integrar los siguientes procesos:
- información de pasajeros
- operaciones de vuelo
- reservas y venta de boletos
- programas de fidelización
- control de abordaje
- procesamiento de pagos y facturación

# Clasificación de entidades
El modelo de datos se compone de tre tipos principales de entidades:
1. Entidades de referencia o catálogos
- reservation_status
- ticket_status
- payment_status
- fare_class
- maintenance_type
- customer_category

2. Entidades maestras
- person
- airport
- aircraft
- flight
- customer
- airline
  
3. Entidades transaccionales
- reservation
- ticket
- payment
- invoice
- check_in
- boarding_pass

# Relaciones entre dominios
Los diferentes dominios del sistema se encuentra interconectados de la siguiente manera:
- El dominio Identidad proporciona información de personas utilizada por Clientes, Seguridad y Ventas.
- El dominio Clientes y fidelización utiliza la información de personas para gestionar cuentas de clientes y programas de millas.
- El dominio Ventas y reservas se relaciona con Operaciones de vuelo para asociar reservas y boletos a vuelos específicos.
- El dominio Abordaje utiliza la información de Ventas y reservas para validar pasajeros y generar pases de abordaje.
- El dominio Pagos registra las transacciones financieras derivadas de las ventas.
- El dominio Facturación genera documentos contables a partir de las transacciones registradas en pagos.

# Flujo principal del negocio
El funcionamiento general del sistema sigue el siguiente flujo:
1. Un cliente realiza una reserva de un vuelo.
2. El sistema genera una venta y posteriormente un boleto (ticket) asociado al pasajero.
3. El cliente realiza el pago correspondiente a la compra.
4. El sistema genera la factura de la transacción.
5. Antes del vuelo, el pasajero realiza el check-in.
6. Se asigna un asiento y se registra el equipaje.
7. Se genera el boarding pass para el proceso de abordaje.
8. Finalmente, el pasajero aborda el vuelo programado.

# Reglas de nogicio principales 
- Un cliente puede tener múltiples reservas.
- Una reserva puede incluir varios pasajeros.
- Cada ticket corresponde a un pasajero específico y a un segmento de vuelo.
- Un pasajero debe completar el proceso de check-in para obtener su pase de abordaje.
- Cada pago puede generar una factura asociada.
- Los clientes inscritos en el programa de fidelización pueden acumular millas por sus vuelos.

# Dominios funcionales identificados 
La base de datos está segmentada por los siguientes sub-dominios:
- Datos geográficos: ubicación y direcciones
- Aerolínea: información de aerolineas
- Identidad: información de personas
- Seguridad: usuarios y control de acceso
- Clientes y fidelización: clientes y millas
- Aeropuertos: infraestructura aeroportuaria
- Aeronaves: flota y mantenimiento
- Operación de vuelo: gestión de vuelos
- Ventas, reservas y boletas: comercialización de pasajes
- Abordaje: proceso de embarque
- Pagos: procesamiento financiero
- Facturación: facturas e impuestos

# Dominios específicos con sus respectivas entidades
### Dominio geográfico 
Número de entidades: 8
Entidades principales:
- time_zone
- continent
- country
- state_province
- city
- district
- address
- currency

### Dominio de aerolínea 
Número de entidades: 1
Entidades principales:
- airline
  
### Dominio de identidad
Número de entidades: 6
Entidades principales:
- person_type
- document_type
- contact_type
- person
- person_document
- person_contact

### Dominio de seguridad
Entidades principales: 6
- user_status
- security_role
- security_permission
- user_account
- user_role
- role_permission

### Dominio de clientes y fidelización 
Número de entidades: 9
Entidades principales:
- customer_category
- benefit_type
- loyalty_program
- loyalty_tier
- customer
- loyalty_account
- loyalty_account_tier
- miles_transaction
- customer_benefit

### Dominio de aeropuertos
Número de entidades: 5
Entidades principales:
- airport
- terminal
- boarding_gate
- runway
- airport_regulation

### Dominio de aeronaves 
Número de entidades: 9
Entidades principales:
- aircraft_manufacturer
- aircraft_model
- cabin_class
- aircraft
- aircraft_cabin
- aircraft_seat
- maintenance_provider
- maintenance_type
- maintenance_event

### Dominio de operaciones de vuelo
Número de entidades: 5
Entidades principales:
- flight_status
- delay_reason_type
- flight
- flight_segment
- flight_delay


### Dominio de ventas, reservas y boletas
Número de entidades: 12
Entidades principales:
- reservation_status
- sale_channel
- fare_class
- fare
- ticket_status
- reservation
- reservation_passenger
- sale
- ticket
- ticket_segment
- seat_assignment
- baggage

### Dominio de abordaje
Número de entidades: 5
Entidades principales:
- boarding_group
- check_in_status
- check_in
- boarding_pass
- boarding_validation

### Dominio de pagos
Número de entidades: 5
Entidades principales:
- payment_status
- payment_method
- payment
- payment_transaction
- refund

### Dominio de facturación 
Número de entidades: 5
Entidades principales:
- tax
- exchange_rate
- invoice_status
- invoice
- invoice_line

# Entidades raíz del negocio
Entidades principales:
- reservation
- flight
- aircraft
- customer
- loyalty_account
- invoice
- payment
