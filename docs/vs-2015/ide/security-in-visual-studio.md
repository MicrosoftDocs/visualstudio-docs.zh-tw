---
title: 安全性
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8d967bd1f7a425ccd9dda5a938535788d961352f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672884"
---
# <a name="security-in-visual-studio"></a>Visual Studio 中的安全性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

開發應用程式時，從設計到部署的所有層面都應該考慮到安全性。 從一開始就應盡可能安全地執行 Visual Studio。 請參閱[使用者權限](../ide/user-permissions-and-visual-studio.md)。

 為了協助您有效開發安全的應用程式，您應該對安全性概念和開發平台的安全性功能有基本了解， 而且也應該了解安全性編碼技術。

## <a name="understanding-security"></a>了解安全性
 [安全性](https://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)描述 .NET Framework 程式碼存取安全性、以角色為基礎的安全性、安全性原則，和安全性工具。

## <a name="coding-for-security"></a>安全性的編碼
 大部分產生安全性弱點的編碼錯誤，其發生原因是開發人員在處理使用者輸入時做出不正確的假設，或是他們不完全了解其開發中的平台。

 [安全程式碼撰寫方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)提供分類元件以便處理安全性問題的方針。

 [安全性最佳做法](https://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42)討論緩衝區溢位和由 /GS 編譯時間旗標所提供之 Microsoft Visual C++ 安全性檢查功能的完整內容。
