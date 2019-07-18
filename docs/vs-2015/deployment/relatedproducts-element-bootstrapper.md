---
title: '&lt;RelatedProducts&gt;項目 （啟動載入器） |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70afe724be5b782bc90e162fd65f83ad1b0d0d23
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202531"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt;項目 （啟動載入器）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 `RelatedProducts`項目是子系`Product`項目。 它沒有任何屬性。  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct`項目表示目前的產品取決為指定的產品，並為指定的產品，應該在目前之前安裝。 它是子系`RelatedProducts`項目。 A`RelatedProducts`項目可能會有一或多個`DependsOnProduct`項目。  
  
 `DependsOnProduct` 具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Code`|包含的產品，為所指定的程式碼名稱`ProductCode`屬性的`Product`項目。 如需詳細資訊，請參閱 < [\<產品 > 項目](../deployment/product-element-bootstrapper.md)。|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts`項目會定義零或多個`DependsOnProduct`項目，且沒有屬性。 至少一個`DependsOnProduct`此集中之前必須先安裝目前的產品。 A`RelatedProducts`項目可以有零或多個`EitherProducts`項目。  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct`項目表示產品隨附於目前的安裝，而且不需要另外安裝。 它是子系`RelatedProducts`項目。 A`RelatedProducts`項目可能會有一或多個`IncludesProduct`項目。  
  
 `IncludesProduct` 具有下列屬性。  
  
|屬性|說明|  
|---------------|-----------------|  
|`Code`|包含的產品，為所指定的程式碼名稱`ProductCode`屬性的`Product`項目。 如需詳細資訊，請參閱 < [\<產品 > 項目](../deployment/product-element-bootstrapper.md)。|  
  
## <a name="example"></a>範例  
 下列程式碼範例會指定 Microsoft 安裝程式會隨[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，因此將不需要另外安裝。  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<Product> 元素](../deployment/product-element-bootstrapper.md)
