[Index](../../../../Index.md) > [Asset](../../../Asset.md) > [Equipment](../../Equipment.md) > [HVAC_Equipment](../HVAC_Equipment.md) > [Air_Plenum](Air_Plenum.md) > [Return_Air_Plenum](#)
# Return_Air_Plenum

**Display name:** Return Air Plenum<br />
**DTMI:** dtmi:org:brickschema:schema:Brick:Return_Air_Plenum;1

---

## Relationships

### Inherited Relationships
* **[Equipment](../../Equipment.md):** feeds, isFedBy
* **[Asset](../../../Asset.md):** commissionedBy, documentation, hasPart, hasPoint, installedBy, isPartOf, locatedIn, manufacturedBy, mountedOn, servicedBy

---

## Properties

|Name|Display name|Description|Schema|Writable|
|-|-|-|-|-|
|tags|**en**: Tags|**en**: Brick tags associated with this interface.|array (string)|False|
### Inherited Properties
* **[Equipment](../../Equipment.md):** operationalStageCount
* **[Asset](../../../Asset.md):** assetTag, commissioningDate, customTags, externalIds, geometry, initialCost, installationDate, IPAddress, MACAddress, maintenanceInterval, modelNumber, name, serialNumber, turnoverDate, weight

---

## Target Of
### Inherited
* [Asset](../../../Asset.md).hasPart
* [Asset](../../../Asset.md).isPartOf
* [EquipmentCollection](../../../../Collection/AssetCollection/EquipmentCollection/EquipmentCollection.md).includes