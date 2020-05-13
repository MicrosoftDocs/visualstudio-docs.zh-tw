---
title: 所需平臺版本元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701488"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>必需平臺版本元素(可視化工作室範本)
指定專案範本正常工作所需的作業系統的最小版本。 此元素用於創建[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]應用的專案範本。

 該`RequiredPlatformVersion`值與操作系統的版本直接進行比較。 如果`RequiredPlatformVersion`高於作業系統版本,則範本不會顯示在 **「新項目**」對話方塊中。 要為[!INCLUDE[win8](../debugger/includes/win8_md.md)]或更高指定範本,請設置`RequiredPlatformVersion`為 6.2.0。 要為[!INCLUDE[win81](../debugger/includes/win81_md.md)]或更高指定範本,請設置`RequiredPlatformVersion`為 6.3.0。

 指定`RequiredPlatformVersion`|8 的範本與以前[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]的客戶 樣本相容。

 VSTemplate 樣本資料 ...目標平台名稱必需平臺版本

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

|元素|描述|
|-------------|-----------------|
|[樣本平台名稱](../extensibility/templatedata-element-visual-studio-templates.md)|指定專案範本的目標平台。|

## <a name="text-value"></a>文字值
 需要文字值。

## <a name="remarks"></a>備註
 此文字指定範本所需的最小作業系統版本。

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
- [目標平台名稱元素(視覺化工作室範本)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
