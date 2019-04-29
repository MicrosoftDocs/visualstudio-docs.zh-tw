---
title: '&lt;排程&gt;項目 （啟動載入器） |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f6e4ae90dbd36dab4f4df7f72d5ecf57ee04b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927328"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;排程&gt;項目 （啟動載入器）
`Schedules`項目包含`Schedule`項目，定義特定時間所定義的命令`Command`應該執行項目。

## <a name="syntax"></a>語法

```xml
<Schedules>
    <Schedule
        Name
    >
        <BuildList />
        <BeforePackage />
        <AfterPackage />
    </Schedule>
</Schedules>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `Schedules`項目是子系`Product`項目。 每個`Product`項目可能會有最多一個`Schedules`項目。 `Schedules` 項目沒有任何屬性。

## <a name="schedule"></a>排程
 `Schedule`項目是子系`Schedules`項目。 A`Schedules`項目必須至少一個`Schedule`項目。

 `Schedule` 具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`Name`|必要項。 排程項目名稱。 這會對應至`ScheduleName`屬性`Command`項目。 當`Command`參考具名的排程，才會執行所指定的時間在`Schedule`項目。 排程可能也會與相關聯`FailIf`和`BypassIf`項目，限制這些條件的測試指定的排程上執行。 如需詳細資訊，請參閱 < [\<命令 > 項目](../deployment/commands-element-bootstrapper.md)。|

 給定`Schedule`項目可能只有其中一個下列子系。

## <a name="buildlist"></a>BuildList
 `BuildList`元素會指示安裝程式以啟動應用程式啟動後立即執行命令。

## <a name="beforepackage"></a>BeforePackage
 `BeforePackage`元素會指示安裝程式以安裝指定的封裝之前，請執行命令。

## <a name="afterpackage"></a>AfterPackage
 `AfterPackage`元素會指示安裝程式以安裝指定的封裝之後，執行命令。

## <a name="see-also"></a>另請參閱
- [\<產品 > 項目](../deployment/product-element-bootstrapper.md)
- [產品和套件結構描述參考](../deployment/product-and-package-schema-reference.md)