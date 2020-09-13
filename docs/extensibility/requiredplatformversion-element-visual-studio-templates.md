---
title: RequiredPlatformVersion 項目 (Visual Studio 樣板)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 811cf013c7337e032f9ee5a37f9bc38329dff240
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037734"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a> (Visual Studio 範本的 RequiredPlatformVersion 元素) 

指定專案範本正常運作所需之作業系統的最低版本。 這個元素是用於建立應用程式的專案範本 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 。

 `RequiredPlatformVersion`系統會直接與作業系統的版本比較值。 如果高於 `RequiredPlatformVersion` 作業系統版本，則範本不會出現在 [ **新增專案** ] 對話方塊中。 若要指定 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更高版本的範本，請設定 `RequiredPlatformVersion` 為6.2.0。 若要指定 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 或更高版本的範本，請設定 `RequiredPlatformVersion` 為6.3.0。

 指定 `RequiredPlatformVersion` = 8 的範本與先前的客戶 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 範本相容。

 .Vstemplate TemplateData ...。TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>語法

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>屬性和元素

 無。

### <a name="attributes"></a>屬性

 無。

### <a name="child-elements"></a>子元素

 無。

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|指定專案範本的目標平台。|

## <a name="text-value"></a>文字值

 需要文字值。

## <a name="remarks"></a>備註

 此文字指定範本所需的最低作業系統版本。

## <a name="example"></a>範例

 這個範例會指定專案範本以 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更新版本為目標。

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱

- [ (Visual Studio 範本的 TargetPlatformName 元素) ](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
