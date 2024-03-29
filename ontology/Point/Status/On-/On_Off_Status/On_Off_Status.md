[Index](../../../../index.md) > [Point](../../../Point.md) > [Status](../../Status.md) > [On_Status](../On_Status.md) > [On_Off_Status](#)
# On_Off_Status

Indicates the on/off status of a control loop, relay or equipment


**Display name:** On Off Status<br />
**DTMI:** dtmi:org:brickschema:schema:Brick:On_Off_Status;1

---

## Child interfaces
* [Fan_On_Off_Status](Fan-.md)
* [Locally_On_Off_Status](Locally-.md)
* [Motor_On_Off_Status](Motor-.md)
* [Pump_On_Off_Status](Pump-.md)
* [Remotely_On_Off_Status](Remotely-.md)
* [Standby_Unit_On_Off_Status](Standby_Unit-/Standby_Unit_On_Off_Status.md)
* [Start_Stop_Status](Start_Stop_Status/Start_Stop_Status.md)

---

## Relationships

### Inherited Relationships
* **[Point](../../../Point.md):** isPointOf

---

## Properties

### Inherited Properties
* **[Point](../../../Point.md):** aggregate, customProperties, customTags, hasQuantity, hasSubstance, identifiers, name
* **[Status](../../Status.md):** lastKnownValue

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
