---
title: 偵錯期間無法修改設計工具
description: 設計工具無法在進行調試時修改。 查看此 Visual Studio 物件關聯式設計工具 (O/R 設計工具) 訊息的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 244fbcc21c062c50b2f61940a1b43cf17c22761f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866433"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>偵錯期間無法修改設計工具

如果應用程式是以偵錯模式執行，則嘗試修改 **O/R 設計工具** 上的項目時，就會出現這則訊息。 當應用程式在「偵錯工具」模式中執行時， **O/R 設計** 工具會是唯讀的。

若要更正這個錯誤，請選取 [**調試**] 功能表上的 [**停止調試**]。 應用程式會停止偵錯工具，您可以在 **O/R 設計** 工具中修改專案。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
