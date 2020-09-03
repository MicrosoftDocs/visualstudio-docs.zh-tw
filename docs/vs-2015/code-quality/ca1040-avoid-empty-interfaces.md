---
title: CA1040：避免空的介面 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ef6dc666cbc3c26d58358c9b59264f93a7bf184
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548248"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040:避免使用空的介面
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 介面不會宣告任何成員，也不會執行兩個或多個其他的介面。

## <a name="rule-description"></a>規則描述
 介面是用來定義一組可提供行為或程式使用合約的成員。 不論類型出現在繼承階層架構 (Inheritance Hierarchy) 中的何處，任何類型都可以採用介面所描述的功能。 類型會實作介面，方法是提供介面成員的實作。 空的介面不會定義任何成員。 因此，它不會定義可執行檔合約。

 如果您的設計包含型別預期會實作為的空介面，您可能會使用介面做為標記或識別類型群組的方式。 如果此識別會在執行時間發生，則完成這項工作的正確方法是使用自訂屬性。 請使用屬性的存在與否，或屬性的屬性，以識別目標型別。 如果識別碼必須在編譯時期發生，則可以接受使用空的介面。

## <a name="how-to-fix-violations"></a>如何修正違規
 移除介面或新增成員。 如果使用空的介面來標記一組類型，請將介面取代為自訂屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當介面是在編譯時期用來識別一組類型時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示空的介面。

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
