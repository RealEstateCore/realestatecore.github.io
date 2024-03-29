[Index](../../../../../../index.md) > [Point](../../../../../Point.md) > [Parameter](../../../../Parameter.md) > [Limit](../../../Limit.md) > [Min_Limit](../../Min_Limit.md) > [Min_Air_Flow_Setpoint_Limit](../Min_Air_Flow_Setpoint_Limit.md) > [Min_Heating_Supply_Air_Flow_Setpoint_Limit](#)
# Min_Heating_Supply_Air_Flow_Setpoint_Limit

A parameter that places a lower bound on the range of permitted values of a Heating_Supply_Air_Flow_Setpoint.


**Display name:** Min Heating Supply Air Flow Setpoint Limit<br />
**DTMI:** dtmi:org:brickschema:schema:Brick:Min_Heating_Supply_Air_Flow_Setpoint_Limit;1

---

## Child interfaces
* [Min_Occupied_Heating_Supply_Air_Flow_Setpoint_Limit](Min_Occupied_Heating_Supply_Air_Flow_Setpoint_Limit.md)
* [Min_Unoccupied_Heating_Supply_Air_Flow_Setpoint_Limit](Min_Unoccupied_Heating_Supply_Air_Flow_Setpoint_Limit.md)

---

## Relationships

### Inherited Relationships
* **[Point](../../../../../Point.md):** isPointOf

---

## Properties

### Inherited Properties
* **[Parameter](../../../../Parameter.md):** lastKnownValue
* **[Point](../../../../../Point.md):** aggregate, customProperties, customTags, hasQuantity, hasSubstance, identifiers, name

---

## Target Of
### General
* [Point](../../../../../Point.md).isPointOf
* [Agent](../../../../../../Agent/Agent.md).owns
* [Space](../../../../../../Space/Space.md).isLocationOf
* [Equipment](../../../../../../Asset/Equipment/Equipment.md).feeds
* [Equipment](../../../../../../Asset/Equipment/Equipment.md).isFedBy
* [System](../../../../../../Collection/System/System.md).includes
* [Architecture](../../../../../../Space/Architecture/Architecture.md).isFedBy
* [Document](../../../../../../Information/Document/Document.md).documentTopic
* [Document](../../../../../../Information/Document/Document.md).url
* [Lease](../../../../../../Event/Lease.md).leaseOf
* [PointOfInterest](../../../../../../Information/PointOfInterest.md).objectOfInterest
* [Portfolio](../../../../../../Collection/Portfolio.md).includes
* [ServiceObject](../../../../../../Information/ServiceObject/ServiceObject.md).relatedTo
* [Meter](../../../../../../Asset/Equipment/Meter/Meter.md).meters
### Inherited
* [ActuationEvent](../../../../../../Event/Point-/ActuationEvent.md).targetPoint
* [Architecture](../../../../../../Space/Architecture/Architecture.md).hasPoint
* [Asset](../../../../../../Asset/Asset.md).hasPoint
* [ExceptionEvent](../../../../../../Event/Point-/ExceptionEvent.md).sourcePoint
* [ObservationEvent](../../../../../../Event/Point-/ObservationEvent/ObservationEvent.md).sourcePoint
* [ServiceObject](../../../../../../Information/ServiceObject/ServiceObject.md).producedBy
