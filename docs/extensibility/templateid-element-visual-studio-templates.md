---
title: TemplateID 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1f992d9f501b965fc300b97613a3d6f3bd4e35d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62798955"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 項目 (Visual Studio 範本)
指定分類的群組中的項目範本的項目範本的識別碼[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)項目。

 \<VSTemplate> \<TemplateData> \<TemplateID>

## <a name="syntax"></a>語法

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 A`string`歸類為一組項目範本的項目範本的識別項表示`TemplateGroupID`項目。

## <a name="remarks"></a>備註
 `TemplateID` 是選擇性項目。

 .Vstemplate 檔案遺漏`TemplateID`項目，則[名稱](../extensibility/name-element-visual-studio-templates.md)項目當做識別碼使用的範本。

 值`TemplateID`項目搭配專案系統登錄 (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) 來篩選範本，會出現在**加入新項目** 對話方塊。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)