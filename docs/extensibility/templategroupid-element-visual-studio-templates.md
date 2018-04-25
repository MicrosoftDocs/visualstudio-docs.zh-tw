---
title: TemplateGroupID 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91631975d48f6e7e13646c428cdd5b5473bbeed2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID 項目 (Visual Studio 範本)
指定要顯示哪一種專案項目範本。 這個項目時，重要[ShowByDefault （Visual Studio 範本）](../extensibility/showbydefault-visual-studio-templates.md)設`false`。 當[ShowByDefault （Visual Studio 範本）](../extensibility/showbydefault-visual-studio-templates.md)設`true`，則是所有專案類型中可用的項目範本。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateGroupID >  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 文字可指定某個類別的項目範本的識別碼。  
  
## <a name="remarks"></a>備註  
 `TemplateGroupID` 是元素。  
  
 值`TemplateGroupID`搭配專案系統登錄項目 (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<版本號碼 >* \Projects\\)篩選的範本中出現的**加入新項目** 對話方塊。  
  
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
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)