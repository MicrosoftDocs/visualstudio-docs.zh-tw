---
title: CA2212：不要以 WebMethod 標記 Serviced 元件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67d2e2790db4a3e8061dcd949b79c127e67f022d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922713"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212：不要以 WebMethod 標記 Serviced 元件
|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|分類|Microsoft.Usage|
|中斷變更|中斷|

## <a name="cause"></a>原因
 繼承自類型中的方法<xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>會標示<xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 <xref:System.Web.Services.WebMethodAttribute> 適用於使用 ASP.NET，所建立的 XML Web 服務中的方法它會將方法呼叫從遠端的 Web 用戶端。 方法和類別必須是公用、 ASP.NET Web 應用程式中執行。 <xref:System.EnterpriseServices.ServicedComponent> 型別所裝載的 COM + 應用程式，且可以使用 COM + 服務。 <xref:System.Web.Services.WebMethodAttribute> 不會套用到<xref:System.EnterpriseServices.ServicedComponent>類型，因為它們不能針對相同的案例。 具體來說，加入至屬性<xref:System.EnterpriseServices.ServicedComponent>方法不會方法呼叫從遠端的 Web 用戶端。 因為<xref:System.Web.Services.WebMethodAttribute>和<xref:System.EnterpriseServices.ServicedComponent>方法具有衝突的行為和需求，內容和異動流程，方法的行為可能會在某些情況下不正確。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除該屬性從<xref:System.EnterpriseServices.ServicedComponent>方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 沒有案例會正確組合這些項目。

## <a name="see-also"></a>另請參閱
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>