---
title: 在進行調試時，無法修改設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8e393ad46b6d37bd74806a0a4b84825bd059457
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672267"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>偵錯期間無法修改設計工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果應用程式是以偵錯模式執行，則嘗試修改 O/R Designer 上的項目時，就會出現這則訊息。 如果應用程式是以偵錯模式執行，則 O/R Designer 會是唯讀的。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 按一下 [**調試**] 功能表上的 [**停止調試**]。

     應用程式會停止偵錯，而 O/R Designer 中的項目會成為可修改的狀態。

## <a name="see-also"></a>請參閱
 [LINQ to SQL 中的工具 Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [逐步解說：建立 LINQ to SQL 類別（O-R 設計工具）](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
