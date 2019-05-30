---
title: TemplateGroupID 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b4e0ccae38b79cf8efb4b7b426fb65ae909c5d5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316597"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID 項目 (Visual Studio 範本)
指定要顯示哪一種專案項目範本。 這個項目時，重要[ShowByDefault （Visual Studio 範本）](../extensibility/showbydefault-visual-studio-templates.md)設定為`false`。 當[ShowByDefault （Visual Studio 範本）](../extensibility/showbydefault-visual-studio-templates.md)設定為`true`，則項目範本會提供在所有專案類型。

 \<VSTemplate> \<TemplateData> \<TemplateGroupID>

## <a name="syntax"></a>語法

```
<TemplateGroupID> ... </TemplateGroupID>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字可指定某個類別的項目範本的識別碼。

## <a name="remarks"></a>備註
 `TemplateGroupID` 是元素。

 值`TemplateGroupID`項目搭配專案系統登錄 (hkey_local_machine\software\microsoft\visualstudio\\ *\<版本號碼>* \Projects\\)會出現在篩選器範本 **加入新項目** 對話方塊。

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