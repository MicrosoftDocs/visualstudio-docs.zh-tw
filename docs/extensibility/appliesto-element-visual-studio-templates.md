---
title: AppliesTo 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e27ee1ab0ba42a82d61e2adbe9fb4c6c81cbb48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo 項目 (Visual Studio 樣板)
指定用於比對一個或多個功能的選擇性運算式  (請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>)。 專案類型會透過階層架構將功能公開為 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5> 屬性。 如此一來，範本就可以在具有通用功能的多個專案類型之間共用。  
  
 這是選擇性的項目。 一個範本檔最多只能有一個執行個體。 這個項目只會根據目前選取的現用專案，讓項目範本加入成為適用的範本。 它不能用來讓項目範本變成不適用。 如果 `AppliesTo` 不存在或運算式未成功選擇加入，則會使用 `TemplateID` 或 `TemplateGroupID` 讓範本成為適用，就如舊版產品一樣。  
  
 已在 Visual Studio 2013 Update 2 中引入。 若要參考的正確版本，請參閱[參考組件提供在 Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb)。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<AppliesTo >  
  
## <a name="syntax"></a>語法  
  
```  
<AppliesTo>Capability1</AppliesTo>   
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。 此文字會指定專案的功能。  
  
 有效的運算式語法定義如下：  
  
-   功能運算式，例如"(VisualC &#124; CSharp) + (MSTest &#124; NUnit)"。  
  
-   「&#124;"是 OR 運算子。  
  
-   "&" 和 "+" 字元都是 AND 運算子。  
  
-   "!" 字元是 NOT 運算子。  
  
-   括號會強制執行評估優先順序。  
  
-   Null 或空白運算式會判斷值為相符項目。  
  
-   專案功能可以是下列這些保留字元以外的任何字元:"':;,+-*/\\！ ~&#124;& %$@^()={} [] <> 嗎？ \t\b\n\r  
  
## <a name="example"></a>範例  
 下列範例將示範三個不同的範本。 `Template1` 適用於所有 C# 專案類型，或是任何支援 `WindowsAppContainer` 功能的其他專案類型。 `Template2` 適用於任何類型的所有 C# 專案。 `Template3` 適用於不是 `WindowsAppContainer` 專案的 C# 專案。  
  
```xml  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 2 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)