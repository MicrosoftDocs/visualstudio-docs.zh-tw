---
title: '&lt;排程&gt;元素 （啟動載入器） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c551bc9335dc41f82800e2c3435d8508967a6db
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815466"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;排程&gt;元素 （啟動載入器）
`Schedules`元素包含`Schedule`項目，可定義特定時間所定義的命令在`Command`應該執行項目。  
  
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
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `Schedules`元素是子系`Product`項目。 每個`Product`元素可能會有最多一個`Schedules`項目。 `Schedules`項目沒有任何屬性。  
  
## <a name="schedule"></a>排程  
 `Schedule`元素是子系`Schedules`項目。 A`Schedules`元素必須至少一個`Schedule`項目。  
  
 `Schedule` 具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要。 排程項目名稱。 這會對應至`ScheduleName`屬性`Command`項目。 當`Command`參考具名的排程，就只會執行它時，由`Schedule`項目。 可能也與相關聯的排程`FailIf`和`BypassIf`項目，這些條件的測試限制於指定的排程執行。 如需詳細資訊，請參閱[\<命令 > 項目](../deployment/commands-element-bootstrapper.md)。|  
  
 給定`Schedule`元素能有正好一個下列子節點。  
  
## <a name="buildlist"></a>BuildList  
 `BuildList`項目會指示安裝程式啟動載入應用程式啟動後立即執行命令。  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage`項目會指示安裝程式以安裝指定的封裝之前，請執行命令。  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage`項目會指示安裝程式以安裝指定的封裝之後，執行命令。  
  
## <a name="see-also"></a>另請參閱  
 [\<產品 > 項目](../deployment/product-element-bootstrapper.md)   
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)