---
title: " (Visual Studio 範本的 TemplateID 元素) |Microsoft Docs"
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699061"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 項目 (Visual Studio 範本)
指定專案範本的識別碼，該專案範本會依 [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) 元素分類為一組專案範本。

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

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

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 `string`，表示專案樣板的識別碼，該專案範本會依專案分類為專案範本群組 `TemplateGroupID` 。

## <a name="remarks"></a>備註
  是選擇性元素。

 如果 .vstemplate 檔案省略了 `TemplateID` 元素，則 [Name](../extensibility/name-element-visual-studio-templates.md) 元素會當做範本的識別碼使用。

 專案的值 `TemplateID` 會與 project system 註冊 (HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\11.0\projects \\) 來篩選出現在 [ **加入新專案** ] 對話方塊中的範本。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
