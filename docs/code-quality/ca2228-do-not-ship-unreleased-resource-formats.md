---
title: "CA2228： 不要格式建置的資源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 959d88751ff250e54f6a3f89f0b4b0554add96d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228：不要使用尚未發行版本所支援的格式建置資源
|||  
|-|-|  
|TypeName|DoNotShipUnreleasedResourceFormats|  
|CheckId|CA2228|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 資源檔所使用的版本建立[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，目前不支援。  
  
## <a name="rule-description"></a>規則描述  
 使用發行前版本所建置的資源檔[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可能不支援的.NET framework 版本。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，建置使用的支援的版本的資源[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。