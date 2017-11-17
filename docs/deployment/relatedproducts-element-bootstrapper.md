---
title: "&lt;RelatedProducts&gt;元素 （啟動載入器） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4fa304f787c954b9ee89878e792e6f543f344f60
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt;元素 （啟動載入器）
`RelatedProducts`項目定義，或是相依於目前的產品中包含其他產品。  
  
## <a name="syntax"></a>語法  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `RelatedProducts`元素是子系`Product`項目。 它沒有任何屬性。  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct`項目表示目前產品定為指定的產品，並為指定的產品應該在之前目前的安裝。 它是子節點的`RelatedProducts`項目。 A`RelatedProducts`元素可能會有一或多個`DependsOnProduct`項目。  
  
 `DependsOnProduct`具有下列屬性。  
  
|屬性|說明|  
|---------------|-----------------|  
|`Code`|包含產品中，所指定的程式碼名稱`ProductCode`屬性`Product`項目。 如需詳細資訊，請參閱[\<產品 > 項目](../deployment/product-element-bootstrapper.md)。|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts`元素可定義零或多個`DependsOnProduct`項目，並沒有任何屬性。 至少一個`DependsOnProduct`此集中之前必須先安裝目前的產品。 A`RelatedProducts`元素可以有零或多個`EitherProducts`項目。  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct`項目表示產品隨附於目前的安裝，而且不需要另外安裝。 它是子節點的`RelatedProducts`項目。 A`RelatedProducts`元素可能會有一或多個`IncludesProduct`項目。  
  
 `IncludesProduct`具有下列屬性。  
  
|屬性|說明|  
|---------------|-----------------|  
|`Code`|包含產品中，所指定的程式碼名稱`ProductCode`屬性`Product`項目。 如需詳細資訊，請參閱[\<產品 > 項目](../deployment/product-element-bootstrapper.md)。|  
  
## <a name="example"></a>範例  
 下列程式碼範例會指定 Microsoft 安裝程式會隨[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，因此將不需要另外安裝。  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<產品 > 項目](../deployment/product-element-bootstrapper.md)