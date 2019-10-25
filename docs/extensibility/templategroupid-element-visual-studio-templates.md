---
title: TemplateGroupID 元素（Visual Studio 範本） |Microsoft Docs
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
ms.openlocfilehash: 7f710a73d8b9c4e31c8189d3322c518f20def5bb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718662"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID 項目 (Visual Studio 範本)
指定要顯示哪一種專案項目範本。 當[ShowByDefault （Visual Studio 範本）](../extensibility/showbydefault-visual-studio-templates.md)設定為 `false` 時，這個元素很重要。 當[[ShowByDefault （Visual Studio 範本）](../extensibility/showbydefault-visual-studio-templates.md) ] 設定為 [`true`] 時，就會在所有專案類型中使用專案範本。

 \<VSTemplate > \<TemplateData > \<TemplateGroupID >

## <a name="syntax"></a>語法

```
<TemplateGroupID> ... </TemplateGroupID>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子項目
 無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案] 或 [加入新項目] 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字可指定某個類別的項目範本的識別碼。

## <a name="remarks"></a>備註
 `TemplateGroupID` 是元素。

 @No__t_0 元素的值會與專案系統註冊（HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<version 號碼 >* \Projects \\）一起使用，以篩選出現在**加入新專案中的範本**對話方塊。

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

## <a name="see-also"></a>請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)