---
title: '&lt;RelatedProducts&gt;項目 （啟動載入器） |Microsoft Docs'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42756b21e631ec14e9c590833f6f0e95a317cc22
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747463"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt;項目 （啟動載入器）
`RelatedProducts`項目定義，或是相依於目前的產品中包含其他產品。

## <a name="syntax"></a>語法

```xml
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

|屬性|描述|
|---------------|-----------------|
|`Code`|包含的產品，為所指定的程式碼名稱`ProductCode`屬性的`Product`項目。 如需詳細資訊，請參閱 < [\<產品 > 項目](../deployment/product-element-bootstrapper.md)。|

## <a name="example"></a>範例
 下列程式碼範例會指定 Microsoft 安裝程式會隨.NET Framework 中，並因此不需要另外安裝。

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>另請參閱
- [\<產品 > 項目](../deployment/product-element-bootstrapper.md)