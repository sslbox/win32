---
Description: Creates an empty skin mesh object using a declarator.
ms.assetid: 5356cfe5-de90-462d-9722-72f3618decfb
title: D3DX10CreateSkinInfo function
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# D3DX10CreateSkinInfo function

Creates an empty skin mesh object using a declarator.

## Syntax


```C++
HRESULT D3DX10CreateSkinInfo(
  _Out_ LPD3DX10SKININFO *ppSkinInfo
);
```



## Parameters

<dl> <dt>

*ppSkinInfo* \[out\]
</dt> <dd>

Type: **[**LPD3DX10SKININFO**](id3dx10skininfo.md)\***

Address of a pointer to an [**ID3DX10SkinInfo Interface**](id3dx10skininfo.md), representing the created skin mesh object.

</dd> </dl>

## Return value

Type: **[**HRESULT**](https://msdn.microsoft.com/en-us/library/Bb401631(v=MSDN.10).aspx)**

If the function succeeds, the return value is D3D\_OK. If the function fails, the return value can be: E\_OUTOFMEMORY.

## Remarks

Use the [**ID3DX10SkinInfo::SetBoneInfluence**](id3dx10skininfo-setboneinfluence.md) to populate the empty skin mesh object returned by this method.

## Requirements



|                    |                                                                                         |
|--------------------|-----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX10Mesh.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3DX10.lib</dt> </dl>   |



## See also

<dl> <dt>

[Mesh Functions](d3d10-graphics-reference-d3dx10-functions-mesh.md)
</dt> <dt>

[D3DX Functions](d3d10-graphics-reference-d3dx10-functions.md)
</dt> </dl>

 

 



