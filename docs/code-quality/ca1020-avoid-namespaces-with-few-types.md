---
title: "CA1020： 避免在命名空間與一些類型，|Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ae5f1693fc00bca0068d66c20e64655b5f7ea106
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020：避免在命名空間中包含過少的類型
|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 全域命名空間以外的命名空間包含少於五個型別。  
  
## <a name="rule-description"></a>規則描述  
 請確定每個命名空間具有邏輯組織，並且將存在合理的理由沒有嚴密填入的命名空間中的類型。 命名空間應該包含在大部分情況下一起使用的類型。 互斥其應用程式時，類型應該位於個別的命名空間。 例如，<xref:System.Web.UI>命名空間包含的 Web 應用程式中使用的類型和<xref:System.Windows.Forms>命名空間包含類型，用於[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-架構的應用程式。 即使兩個命名空間類型，可控制使用者介面的層面，這些類型並未設計成使用相同的應用程式中。 因此，它們位於不同的命名空間中。 因為這會增加一項功能的可搜尋性，謹慎命名空間的組織可以也很有用。 藉由檢查命名空間階層架構，程式庫的取用者應該能夠找出實作功能的類型。  
  
> [!NOTE]
>  設計階段型別和權限不應該合併至其他命名空間，以符合這項指導方針。 這些型別屬於自己的命名空間下主要命名空間，且命名空間應該結尾`.Design`和`.Permissions`分別。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請嘗試結合到單一命名空間包含幾個類型的命名空間。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，命名空間不包含其他的命名空間中的型別搭配使用的型別時。