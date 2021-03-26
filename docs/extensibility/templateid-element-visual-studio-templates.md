---
title: " (Visual Studio 範本的 TemplateID 元素) |Microsoft Docs"
description: 深入瞭解 TemplateID 元素，以及它如何指定專案範本的識別碼，該範本會依 TemplateGroupID 元素分類為一組專案範本。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e33f2d5c424e5d48cff212dc736bbc13e58801d5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056008"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 項目 (Visual Studio 範本)
指定專案範本的識別碼，該專案範本會依 [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) 元素分類為一組專案範本。

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Syntax

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 `string`，表示專案樣板的識別碼，該專案範本會依專案分類為專案範本群組 `TemplateGroupID` 。

## <a name="remarks"></a>備註
  是選擇性元素。

 如果 .vstemplate 檔案省略了 `TemplateID` 元素，則 [Name](../extensibility/name-element-visual-studio-templates.md) 元素會當做範本的識別碼使用。

 專案的值 `TemplateID` 會與 project system 註冊 (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects一起使用 \\) 來篩選出現在 [ **加入新專案** ] 對話方塊中的範本。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
