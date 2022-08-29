[Index](../../../Index.md) > [Asset](../../Asset.md) > [Equipment](../Equipment.md) > [PV_Panel](#)
# PV_Panel

**Display name:** PV Panel<br />
**DTMI:** dtmi:org:brickschema:schema:Brick:PV_Panel;1

---

## Child interfaces
* [PVT_Panel](../Solar_Thermal_Collector/PVT_Panel.md)

---

## Relationships

### Inherited Relationships
* **[Equipment](../Equipment.md):** feeds, isFedBy
* **[Asset](../../Asset.md):** commissionedBy, documentation, hasPart, hasPoint, installedBy, isPartOf, locatedIn, manufacturedBy, mountedOn, servicedBy

---

## Properties

|Name|Display name|Description|Schema|Writable|
|-|-|-|-|-|
|measuredModuleConversionEfficiency|**en**: Measured module conversion efficiency||Microsoft.Azure.DigitalTwins.Parser.Models.DTObjectInfo|True|
|ratedModuleConversionEfficiency|**en**: Rated module conversion efficiency||Microsoft.Azure.DigitalTwins.Parser.Models.DTObjectInfo|True|
### Inherited Properties
* **[Equipment](../Equipment.md):** operationalStageCount
* **[Asset](../../Asset.md):** assetTag, commissioningDate, customTags, externalIds, geometry, initialCost, installationDate, IPAddress, MACAddress, maintenanceInterval, modelNumber, name, serialNumber, turnoverDate, weight

---

## Target Of
### Inherited
* [Asset](../../Asset.md).hasPart
* [Asset](../../Asset.md).isPartOf
* [EquipmentCollection](../../../Collection/AssetCollection/EquipmentCollection/EquipmentCollection.md).includes
