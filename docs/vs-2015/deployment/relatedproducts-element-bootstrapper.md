---
title: '&lt;啟動載入器 &gt;)  (RelatedProducts 元素 |Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202531"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;啟動載入器 &gt;)  (RelatedProducts 元素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`RelatedProducts`元素會定義相依于或包含在目前產品中的其他產品。  
  
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
  
## <a name="elements-and-attributes"></a>元素和屬性  
 `RelatedProducts`元素是元素的子系 `Product` 。 它沒有任何屬性。  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct`元素表示目前的產品取決於已命名的產品，而且應該在目前的產品之前安裝命名產品。 它是專案的子系 `RelatedProducts` 。 `RelatedProducts`元素可能有一或多個 `DependsOnProduct` 元素。  
  
 `DependsOnProduct` 具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Code`|所含產品的代碼名稱，如元素的屬性所指定 `ProductCode` `Product` 。 如需詳細資訊，請參閱[ \<Product> 元素](../deployment/product-element-bootstrapper.md)。|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts`元素定義零或多個 `DependsOnProduct` 元素，而且沒有任何屬性。 在 `DependsOnProduct` 目前的產品之前，必須先安裝此集合中至少一個。 `RelatedProducts`元素可以有零或多個 `EitherProducts` 元素。  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct`元素表示產品隨附于目前的安裝，而且不需要個別安裝。 它是專案的子系 `RelatedProducts` 。 `RelatedProducts`元素可能有一或多個 `IncludesProduct` 元素。  
  
 `IncludesProduct` 具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Code`|所含產品的代碼名稱，如元素的屬性所指定 `ProductCode` `Product` 。 如需詳細資訊，請參閱[ \<Product> 元素](../deployment/product-element-bootstrapper.md)。|  
  
## <a name="example"></a>範例  
 下列程式碼範例會指定使用安裝 Microsoft 安裝程式 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ，因此不需要個別安裝。  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<Product> 元素](../deployment/product-element-bootstrapper.md)
