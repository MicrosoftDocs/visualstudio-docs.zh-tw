---
title: 樣本組 ID 元素(可視化工作室範本) |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: affc324418e3745f85fb0b91a0ef7abda0ab28b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699070"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID 項目 (Visual Studio 範本)
指定要顯示哪一種專案項目範本。 當[ShowByDefault(可視化工作室範本)](../extensibility/showbydefault-visual-studio-templates.md)`false`設置為 時,此元素非常重要。 當[ShowByDefault(可視化工作室範本)](../extensibility/showbydefault-visual-studio-templates.md)`true`設置為 時,專案範本在所有項目類型中都可用。

 \<樣本>\<範本資料>\<範本組id>

## <a name="syntax"></a>語法

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字可指定某個類別的項目範本的識別碼。

## <a name="remarks"></a>備註
 `TemplateGroupID` 是元素。

 元素的值`TemplateGroupID`與專案系統註冊(HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio\\*\<版本號>*[專案\\]一起使用,以篩選「**添加新專案」** 對話框中顯示的範本。

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
