---
title: Bitmap 元素 |Microsoft Docs
description: Bitmap 元素會定義點陣圖。 點陣圖是從資源或檔案載入的。 本文包含範例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe9002c3da63e9570819588035395780715e1d64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941862"
---
# <a name="bitmap-element"></a>Bitmap 元素
定義點陣圖。 點陣圖是從資源或檔案載入的。

## <a name="syntax"></a>Syntax

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/識別碼命令識別碼的 GUID。<br /><br /> 點陣圖的 guid 屬性與任何 VSPackage 或其他命令群組沒有關聯。  它應該是點陣圖定義的唯一的，而且不應該用於任何其他用途。|
|渣 油|GUID/識別碼命令識別碼的識別碼。 必須是 resID 或 href 屬性。<br /><br /> ResID 屬性是一個整數資源識別碼，可決定要在命令表格合併期間載入的點陣圖區。  載入命令資料表時，將會從相同模組的資源載入資源識別碼所指定的點陣圖。|
|usedList|如果 resID 屬性存在，則為必要項。 選取點陣圖條紋中的可用影像。|
|href|點陣圖的路徑。 必須是 resID 或 href 屬性。<br /><br /> 會搜尋包含路徑中指出的影像檔案，並將其內嵌在產生的二進位檔中。  在命令表格合併期間，會複製影像，而不需要額外的資源查閱或載入。  如果 usedList 屬性不存在，則會提供帶狀中的所有影像。 **注意：**  影像可能會以數種格式提供，包括 *.bmp*、 *.png* 和 *.gif*。  舊版編譯器不支援具有部分透明度之 Alpha 資訊的32位點陣圖影像。 這些版本的因應措施是使用 *.png* 格式。|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[點陣圖元素](../extensibility/bitmaps-element.md)|群組點陣圖元素。|

## <a name="example"></a>範例

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
