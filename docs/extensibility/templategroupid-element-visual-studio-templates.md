---
title: " (Visual Studio 範本的 TemplateGroupID 元素) |Microsoft Docs"
description: 瞭解 TemplateGroupID 元素，以及它如何指定專案範本會顯示在哪種專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9db0d2744648901a9389bd2d2805d8c6a4073ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895358"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID 項目 (Visual Studio 範本)
指定要顯示哪一種專案項目範本。 當 [ () 的 Visual Studio 範本 ](../extensibility/showbydefault-visual-studio-templates.md) 設定為時，這個元素相當重要 `false` 。 當 [ShowByDefault (Visual Studio 範本) ](../extensibility/showbydefault-visual-studio-templates.md) 設定為時 `true` ，所有專案類型都可使用專案範本。

 \<VSTemplate> \<TemplateData>
 \<TemplateGroupID>

## <a name="syntax"></a>Syntax

```
<TemplateGroupID> ... </TemplateGroupID>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字可指定某個類別的項目範本的識別碼。

## <a name="remarks"></a>備註
 `TemplateGroupID` 是元素。

 元素的值 `TemplateGroupID` 會與專案系統註冊一起使用 ( # B0 \\ *\<version number>* \Projects \\) ，以篩選出現在 [**加入新專案**] 對話方塊中的範本。

|Visual C++ 值|意義|
|------------------------|-------------|
|VC-Native|用於原生專案。 如果無法判斷專案類型，則也是預設值。|
|VC-Managed|用於 Managed (/clr) 專案|
|VC-Windows|用於以 Windows 平台為目標的所有專案 (原生/Managed/市集)|
|WinRT-Native-UAP|用於 Windows 10 市集專案|
|CodeSharing-Native|用於 共用項目專案|
|WinRT-Native-6.3|用於 Windows 8.1 市集專案|
|WinRT-Native-Phone-6.3|用於 Windows Phone 8.1 專案|
|WinRT 原生|用於 Windows 8.0 市集專案|
|VC-Android|用於 Android 專案|

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
