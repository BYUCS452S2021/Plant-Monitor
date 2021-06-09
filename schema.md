# Plant Monitor Schema

## **Tables**

### User
The `User` table models individual end users for the IoT monitor. Each other entity has a many to one relationship with a `User`.

**User (id, email, password, first_name, last_name)**
- Primary Key: `id`

### Plant
The `Plant` table models individual plants which the user adds to their account.

**Plant (id, type, user_id)
- Primary Key: `id`
- Foreign Key: `user_id` references `User.id`


### Device
The `Device` table models the physical IoT Plant Monitor.

**Device (id, name, user_id)**
- Primary Key: `id`
- Foreign Key: `user_id` references `User.id`


### Measurement
The `Measurement` table models individual measurements recorded from the IoT Plant Monitor device.

**Measurement (id, type, value, unit, user_id, device_id, plant_id)**
- Primary Key: `id`
- Foreign Key: `user_id` references `User.id`
- Foreign Key: `device_id` references `Device.id`
- Foreign Key: `plant_id` references `Plant.id`

## Relationships
The following relationships between tables exist:
- `Plant.user_id` (Many) => (1) `User.id`
- `Device.user_id` (Many) => (1) `User.id`
- `Measurement.user_id` (Many) => (1) `User.id`
- `Measurement.device_id` (Many) => (1) `Device.id`
- `Measurement.plant_id` (Many) => (1) `Plant.id`
