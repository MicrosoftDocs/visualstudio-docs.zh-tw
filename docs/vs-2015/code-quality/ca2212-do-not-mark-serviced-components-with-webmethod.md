---
title: CA2212：不要使用 WebMethod 標記已服務的元件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c707fef5562b932b6232300131f6e6e6efef6a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534559"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212:不要以 WebMethod 標記 Serviced 元件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|類別|Microsoft。使用方式|
|中斷變更|中斷|

## <a name="cause"></a>原因
 在繼承自的型別中的方法 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> 會以標記 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 <xref:System.Web.Services.WebMethodAttribute>適用于使用 ASP.NET 所建立之 XML Web Service 中的方法;它可從遠端 Web 用戶端呼叫方法。 方法和類別必須是公用的，而且在 ASP.NET Web 應用程式中執行。 <xref:System.EnterpriseServices.ServicedComponent>類型是由 COM + 應用程式所裝載，而且可以使用 COM + 服務。 <xref:System.Web.Services.WebMethodAttribute>不會套用至 <xref:System.EnterpriseServices.ServicedComponent> 類型，因為它們不適用於相同的案例。 具體而言，將屬性新增至 <xref:System.EnterpriseServices.ServicedComponent> 方法並不會讓方法從遠端 Web 用戶端呼叫。 由於 <xref:System.Web.Services.WebMethodAttribute> 和 <xref:System.EnterpriseServices.ServicedComponent> 方法具有內容和交易流程的衝突行為和需求，因此在某些情況下，方法的行為會不正確。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請從方法中移除該屬性 <xref:System.EnterpriseServices.ServicedComponent> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 沒有任何案例結合這些專案是正確的。

## <a name="see-also"></a>另請參閱
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
