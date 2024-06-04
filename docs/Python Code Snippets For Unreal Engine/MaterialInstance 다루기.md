> [Unreal Engine 5 Code Snippets](../README.md) / [Python Code Snippets For Unreal Engine](README.md) / MaterialInstance 다루기.md
## MaterialInstance 다루기
unreal.MaterialInstanceConstant
unreal.MaterialInstanceBasePropertyOverrides
unreal.MaterialEditingLibrary

```
# ContentBrowser에서 선택된 Material Instance Asset 가져오기
>>> materials = unreal.EditorUtilityLibrary.get_selected_assets()
>>> material = materials[0]
 
# parameter 얻어오기
>>> material.get_scalar_parameter_value('FadeOpacity')
1.0
 
>>> material.texture_parameter_values[0]
<Struct 'TextureParameterValue' (0x0000072F9B817100) {parameter_info: {name: "Add_Normal", association: GlobalParameter, index: -1}, parameter_value: "/Script/Engine.Texture2D'/Game/Environment/NaturalObject/Stone/Rock/BG_Rock_30_02_N.BG_Rock_30_02_N'"}>
 
>>> material.get_texture_parameter_value('DiffuseA')
<Object '/Game/Environment/WorldResource/Landscape/TileTextures/BG_Rock_29_01_Tile_BH.BG_Rock_29_01_Tile_BH' (0x0000072F3C84B600) Class 'Texture2D'>
 
# BlendMode 얻어오기
>>> overrides = material.get_editor_property('base_property_overrides')
>>> overrides.get_editor_property('BlendMode')
<BlendMode.BLEND_MASKED: 1>
 
# BlendMode 설정하기 (override)
>>> overrides.set_editor_property('override_blend_mode', True)
>>> overrides.set_editor_property('BlendMode', unreal.BlendMode.BLEND_ADDITIVE)
 
# parent material 변경하기
>>> parent_material_path = '/Game/Material/BaseMaterial/Material/ENV_Blend_MAT'
>>> parent_material_uasset = unreal.EditorAssetLibrary.load_asset( parent_material_path )
>>> unreal.MaterialEditingLibrary.set_material_instance_parent(material, parent_material_uasset)
 
# scalar값 설정하기 (override)
>>> unreal.MaterialEditingLibrary.set_material_instance_scalar_parameter_value(material, 'FadeOpacity', 99.0)
```