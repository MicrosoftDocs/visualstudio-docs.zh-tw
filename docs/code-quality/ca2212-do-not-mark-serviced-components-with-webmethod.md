---
title: CA2212:不要以 WebMethod 標記 Serviced 元件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b2ace5f6e51fc7a8d29faab14cc2332fd808f93
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231659"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212:不要以 WebMethod 標記 Serviced 元件

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|分類|Microsoft.Usage|
|重大變更|中斷|

## <a name="cause"></a>原因

在繼承自<xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>的型別中的方法會以<xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>標記。

## <a name="rule-description"></a>規則描述

<xref:System.Web.Services.WebMethodAttribute>適用于使用 ASP.NET 所建立之 XML web service 中的方法。它可從遠端 web 用戶端呼叫方法。 方法和類別必須是公用的，而且在 ASP.NET web 應用程式中執行。 <xref:System.EnterpriseServices.ServicedComponent>類型是由 COM + 應用程式所裝載，而且可以使用 COM + 服務。 <xref:System.Web.Services.WebMethodAttribute>不會套用至<xref:System.EnterpriseServices.ServicedComponent>類型，因為它們不適用於相同的案例。 具體而言，將屬性新增至<xref:System.EnterpriseServices.ServicedComponent>方法並不會讓方法從遠端 web 用戶端呼叫。 <xref:System.Web.Services.WebMethodAttribute> 由於<xref:System.EnterpriseServices.ServicedComponent>和方法具有內容和交易流程的衝突行為和需求，因此在某些情況下，方法的行為會不正確。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請從<xref:System.EnterpriseServices.ServicedComponent>方法中移除該屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 沒有任何案例結合這些專案是正確的。

## <a name="see-also"></a>另請參閱

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>