---
title: "CA2137： 透明方法必須包含可驗證的 IL |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3ec0dda4db164f4bd3368f1bb90c782f4aee6024
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137：透明方法必須只包含可驗證的 IL
|||  
|-|-|  
|TypeName|TransparentMethodsMustBeVerifiable|  
|CheckId|CA2137|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 方法包含無法驗證的程式碼，或以傳址方式傳回類型。  
  
## <a name="rule-description"></a>規則描述  
 當安全性透明程式碼嘗試執行無法驗證的 MSIL (Microsoft Intermediate Language) 時，就會引發此規則。 不過，此規則不包含完整的 IL 驗證器，並是使用啟發式來擷取多數的 MSIL 驗證違規情形。  
  
 若要先確定您的程式碼包含只可驗證的 MSIL，執行[Peverify.exe （PEVerify 工具）](/dotnet/framework/tools/peverify-exe-peverify-tool)您的組件。 執行與 PEVerify **/ 透明**選項將輸出限制為只有無法驗證透明方法會導致錯誤。 如果 / 未使用透明選項、 PEVerify 也會確認是否允許包含無法驗證程式碼的重要方法。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，將標記與方法<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性，或移除無法驗證的程式碼。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 在此範例中的方法使用未經驗證的程式碼和應該用來標記<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。  
  
 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]