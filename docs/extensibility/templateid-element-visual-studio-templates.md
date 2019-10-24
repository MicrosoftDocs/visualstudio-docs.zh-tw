---
title: TemplateID 元素（Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0e404921d1ed74db2a1f23117242f49a07206c2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718732"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 項目 (Visual Studio 範本)
指定專案範本的識別碼，該元件分類為專案範本群組（依據[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)元素）。

 \<VSTemplate > \<TemplateData > \<TemplateID >

## <a name="syntax"></a>語法

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案] 或 [加入新項目] 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 @No__t_0，代表專案範本的識別碼，該元件會依照 `TemplateGroupID` 元素分類成專案範本的群組。

## <a name="remarks"></a>備註
 `TemplateID` 是選擇性項目。

 如果 .vstemplate 檔案省略 `TemplateID` 元素，則[Name](../extensibility/name-element-visual-studio-templates.md)元素會當做範本的識別碼使用。

 @No__t_0 元素的值會與專案系統註冊（HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects \\）一起使用，以篩選出現在 [**加入新專案**] 對話方塊中的範本。

## <a name="see-also"></a>請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)