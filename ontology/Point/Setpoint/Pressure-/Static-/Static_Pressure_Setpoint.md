[Index](../../../../index.md) > [Point](../../../Point.md) > [Setpoint](../../Setpoint.md) > [Pressure_Setpoint](../Pressure_Setpoint.md) > [Static_Pressure_Setpoint](#)
# Static_Pressure_Setpoint

Sets static pressure


**Display name:** Static Pressure Setpoint<br />
**DTMI:** dtmi:org:brickschema:schema:Brick:Static_Pressure_Setpoint;1

---

## Child interfaces
* [Building_Air_Static_Pressure_Setpoint](Building_Air-.md)
* [Chilled_Water_Static_Pressure_Setpoint](Chilled_Water-.md)
* [Discharge_Air_Static_Pressure_Setpoint](Discharge_Air-/Discharge_Air_Static_Pressure_Setpoint.md)
* [Exhaust_Air_Static_Pressure_Setpoint](Exhaust_Air-.md)
* [Hot_Water_Static_Pressure_Setpoint](Hot_Water-.md)
* [Static_Pressure_Deadband_Setpoint](Static_Pressure_Deadband_Setpoint/Static_Pressure_Deadband_Setpoint.md)
* [Supply_Air_Static_Pressure_Setpoint](Supply_Air-/Supply_Air_Static_Pressure_Setpoint.md)
* [Underfloor_Air_Plenum_Static_Pressure_Setpoint](Underfloor_Air_Plenum-.md)

---

## Relationships

### Inherited Relationships
* **[Point](../../../Point.md):** isPointOf

---

## Properties

### Inherited Properties
* **[Point](../../../Point.md):** aggregate, customProperties, customTags, hasQuantity, hasSubstance, identifiers, name
* **[Setpoint](../../Setpoint.md):** lastKnownValue

---

## Target Of
### General
* [Point](../../../Point.md).isPointOf
* [Agent](../../../../Agent/Agent.md).owns
* [Space](../../../../Space/Space.md).isLocationOf
* [Equipment](../../../../Asset/Equipment/Equipment.md).feeds
* [Equipment](../../../../Asset/Equipment/Equipment.md).isFedBy
* [System](../../../../Collection/System/System.md).includes
* [Architecture](../../../../Space/Architecture/Architecture.md).isFedBy
* [Document](../../../../Information/Document/Document.md).documentTopic
* [Document](../../../../Information/Document/Document.md).url
* [Lease](../../../../Event/Lease.md).leaseOf
* [PointOfInterest](../../../../Information/PointOfInterest.md).objectOfInterest
* [Portfolio](../../../../Collection/Portfolio.md).includes
* [ServiceObject](../../../../Information/ServiceObject/ServiceObject.md).relatedTo
* [Meter](../../../../Asset/Equipment/Meter/Meter.md).meters
### Inherited
* [ActuationEvent](../../../../Event/Point-/ActuationEvent.md).targetPoint
* [Architecture](../../../../Space/Architecture/Architecture.md).hasPoint
* [Asset](../../../../Asset/Asset.md).hasPoint
* [ExceptionEvent](../../../../Event/Point-/ExceptionEvent.md).sourcePoint
* [ObservationEvent](../../../../Event/Point-/ObservationEvent/ObservationEvent.md).sourcePoint
* [ServiceObject](../../../../Information/ServiceObject/ServiceObject.md).producedBy
