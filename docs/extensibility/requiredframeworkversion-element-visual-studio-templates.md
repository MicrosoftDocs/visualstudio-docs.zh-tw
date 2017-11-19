---
title: "RequiredFrameworkVersion 項目 （Visual Studio 範本） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dfbcc45198381cb111714dfdd52d8846f019e741
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion 項目 (Visual Studio 範本)
指定範本所需的最低.NET Framework 版本。結構描述階層架構。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<RequiredFrameworkVersion >  
  
## <a name="syntax"></a>語法  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義要如何顯示在**新專案**或**加入新項目** 對話方塊。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 文字必須是.NET Framework 所需的範本的最小版本號碼。  
  
## <a name="remarks"></a>備註  
 `RequiredFrameworkVersion` 是選擇性項目。 如果範本只支援特定的最小版本和更新的版本，如果有的話，.NET framework，請使用此項目。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)