---
title: '&lt;排程器元素 (啟動載入器 &gt;) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 85ffab2272a55bfe77c5f2a73c6e25967a203c85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206090"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;排程器元素 (啟動載入器 &gt;) 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Schedules`元素包含 `Schedule` 元素，這些元素 `Command` 會定義應該執行元素所定義之命令的特定時間。  
  
## <a name="syntax"></a>語法  
  
```  
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
 `Schedules`元素是元素的子系 `Product` 。 每個 `Product` 元素最多隻能有一個 `Schedules` 元素。 `Schedules` 項目沒有任何屬性。  
  
## <a name="schedule"></a>排程  
 `Schedule`元素是元素的子系 `Schedules` 。 `Schedules`元素至少必須有一個 `Schedule` 元素。  
  
 `Schedule` 具有下列屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要。 排程專案的名稱。 這會對應至專案的 `ScheduleName` 屬性 `Command` 。 當 `Command` 參考命名排程時，它只會在該元素所指出的時間執行 `Schedule` 。 排程也可以與 `FailIf` 和元素相關聯 `BypassIf` ，這會限制這些條件式測試依指定的排程執行。 如需詳細資訊，請參閱[ \<Commands> 元素](../deployment/commands-element-bootstrapper.md)。|  
  
 指定的專案 `Schedule` 可能只會有下列其中一個子系。  
  
## <a name="buildlist"></a>BuildList  
 `BuildList`元素會指示安裝程式在啟動載入器應用程式之後立即執行命令。  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage`元素會指示安裝程式在安裝指定的封裝之前執行命令。  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage`元素會指示安裝程式在安裝指定的封裝之後，執行命令。  
  
## <a name="see-also"></a>另請參閱  
 [\<Product> 元素](../deployment/product-element-bootstrapper.md)   
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)
