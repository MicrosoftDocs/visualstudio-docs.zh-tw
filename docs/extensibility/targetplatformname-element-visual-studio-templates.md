---
title: TargetPlatformName 元素 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c307a52b8f252f5059f2d4009e98fc4d497f616e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316701"
---
# <a name="targetplatformname-element-visual-studio-templates"></a>TargetPlatformName 項目 (Visual Studio 樣板)
指定專案範本的目標平台。 這個項目用來指定用於建立 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式的專案範本。

## <a name="syntax"></a>語法

```xml
<VSTemplate>
    <TemplateData>
        <TargetPlatformName> OperatingSystem</TargetPlatformName>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|指定專案範本的目標作業系統版本。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

## <a name="remarks"></a>備註
 此文字必須是 **Windows**。

## <a name="example"></a>範例
 這個範例會指定專案範本以 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更新版本為目標。

```xml
<VSTemplate Type="Project" Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
        <RequiredPlatformVersion>8</RequiredPlatformVersion>
    </TemplateData>
    <TemplateContent> </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)