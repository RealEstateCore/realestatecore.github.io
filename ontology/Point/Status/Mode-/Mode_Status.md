[Index](../../../index.md) > [Point](../../Point.md) > [Status](../Status.md) > [Mode_Status](#)
# Mode_Status

Indicates which mode a system, device or control loop is currently in


**Display name:** Mode Status<br />
**DTMI:** dtmi:org:brickschema:schema:Brick:Mode_Status;1

---

## Child interfaces
* [Cooling_Mode_Status](Cooling-/Cooling_Mode_Status.md)
* [Heating_Mode_Status](Heating-/Heating_Mode_Status.md)
* [Occupied_Mode_Status](Occupied-/Occupied_Mode_Status.md)
* [Operating_Mode_Status](Operating-/Operating_Mode_Status.md)
* [Speed_Mode_Status](../Speed-/Speed_Mode_Status.md)
* [Unoccupied_Mode_Status](Unoccupied-/Unoccupied_Mode_Status.md)
* [Zone_Air_Conditioning_Mode_Status](Zone_Air_Conditioning-.md)

---

## Relationships

### Inherited Relationships
* **[Point](../../Point.md):** isPointOf

---

## Properties

### Inherited Properties
* **[Point](../../Point.md):** aggregate, customProperties, customTags, hasQuantity, hasSubstance, identifiers, name
* **[Status](../Status.md):** lastKnownValue

---

## Target Of
### General
* [Point](../../Point.md).isPointOf
* [Agent](../../../Agent/Agent.md).owns
* [Space](../../../Space/Space.md).isLocationOf
* [Equipment](../../../Asset/Equipment/Equipment.md).feeds
* [Equipment](../../../Asset/Equipment/Equipment.md).isFedBy
* [System](../../../Collection/System/System.md).includes
* [Architecture](../../../Space/Architecture/Architecture.md).isFedBy
* [Document](../../../Information/Document/Document.md).documentTopic
* [Document](../../../Information/Document/Document.md).url
* [Lease](../../../Event/Lease.md).leaseOf
* [PointOfInterest](../../../Information/PointOfInterest.md).objectOfInterest
* [Portfolio](../../../Collection/Portfolio.md).includes
* [ServiceObject](../../../Information/ServiceObject/ServiceObject.md).relatedTo
* [Meter](../../../Asset/Equipment/Meter/Meter.md).meters
### Inherited
* [ActuationEvent](../../../Event/Point-/ActuationEvent.md).targetPoint
* [Architecture](../../../Space/Architecture/Architecture.md).hasPoint
* [Asset](../../../Asset/Asset.md).hasPoint
* [ExceptionEvent](../../../Event/Point-/ExceptionEvent.md).sourcePoint
* [ObservationEvent](../../../Event/Point-/ObservationEvent/ObservationEvent.md).sourcePoint
* [ServiceObject](../../../Information/ServiceObject/ServiceObject.md).producedBy
