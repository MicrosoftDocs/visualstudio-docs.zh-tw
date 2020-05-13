---
title: 圖元素 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740004"
---
# <a name="bitmap-element"></a>點陣圖元素
定義點陣圖。 點陣圖從資源或檔載入。

## <a name="syntax"></a>語法

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/ID 命令識別碼的 GUID。<br /><br /> 位圖的 guid 屬性不與任何 VSPackage 或其他命令組關聯。  它應該是位圖定義的唯一,不應用於任何其他目的。|
|渣 油|GUID/ID 命令識別碼的識別碼。 需要 resID 或 href 屬性。<br /><br /> resID 屬性是一個整數資源 ID,用於確定在命令表合併期間要載入的點陣圖條帶。  載入指令表時,資源 ID 指定的點陣圖將從同一模組的資源載入。|
|已使用清單|如果存在 resID 屬性,則為必填項。 選擇點陣圖列中的可用影像。|
|href|位圖的路徑。 需要 resID 或 href 屬性。<br /><br /> 將搜索包含路徑以查找指示的圖像檔,該檔嵌入到生成的二進位檔案中。  在命令表合併期間,將複製映射,無需其他資源查找或載入。  如果使用的 List 屬性不存在,則條帶中的所有圖像都可用。 **註:** 影像可以以多種格式之一提供,包括 *.bmp、.png*和 *.png**.gif*。  早期版本的編譯器不支援具有 Alpha 資訊的 32 位元圖圖像,以便獲得部分透明度。 這些版本的解決方法是使用 *.png*格式。|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[點陣圖元素](../extensibility/bitmaps-element.md)|對位圖元素。|

## <a name="example"></a>範例

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>另請參閱
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
