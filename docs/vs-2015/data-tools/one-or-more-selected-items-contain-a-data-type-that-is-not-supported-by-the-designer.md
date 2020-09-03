---
title: 一或多個選取的專案包含設計工具不支援的資料類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e208b697da1c25dfa2e152ad08096f61c876ebe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658044"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>一個或多個選取的項目包含設計工具不支援的資料類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

從**伺服器總管** / **資料庫總管**拖曳至的一個或多個專案 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 包含 (的不支援的資料類型， [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 例如， [CLR 使用者定義的類型](https://msdn.microsoft.com/library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)) 。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 建立檢視，這個檢視會依據所需的資料表，而且其中只包含受支援的資料型別。

2. 將視圖從**伺服器總管** / **資料庫總管**拖曳至設計工具。

## <a name="see-also"></a>另請參閱
 [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)[逐步解說：建立 LINQ to SQL 類別 (O-R 設計工具) ](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
