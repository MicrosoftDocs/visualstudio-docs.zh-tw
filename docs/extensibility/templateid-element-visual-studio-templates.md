---
title: 樣本 ID 元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8eb5abac9c837b3022354d6da743ac8f21d5e41d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699061"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 項目 (Visual Studio 範本)
指定依[樣本組](../extensibility/templategroupid-element-visual-studio-templates.md)ID 元素分類為一組項樣本的項範本的標識符。

 \<VStemplate>\<範本資料>\<範本ID>

## <a name="syntax"></a>語法

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 表示`string`項範本的標識碼,該項範本`TemplateGroupID`按 元素分類為一組項範本。

## <a name="remarks"></a>備註
  是選擇性元素。

 如果 .vstemplate 檔案省`TemplateID`略了 該元素,則[Name](../extensibility/name-element-visual-studio-templates.md)元素將用作範本的識別碼。

 元素的值`TemplateID`與專案系統註冊(HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio_11.0_\\專案 )一起使用,以篩選"**添加新專案"** 對話框中顯示的範本。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
