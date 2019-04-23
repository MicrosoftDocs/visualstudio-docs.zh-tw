---
title: 一或多個選取的項目包含設計工具不支援的資料類型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac5507722a62942dbca67518c2f6689bf29aacfc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065704"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>一個或多個選取的項目包含設計工具不支援的資料類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

從一或多個項目拖曳**伺服器總管**/**資料庫總管**拖曳至[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]包含不支援的資料型別[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]（比方說，[CLR 使用者定義型別](http://msdn.microsoft.com/library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2))。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 建立檢視，這個檢視會依據所需的資料表，而且其中只包含受支援的資料型別。  
  
2. 將檢視從**伺服器總管**/**資料庫總管**拖曳至設計工具。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [逐步解說：建立 LINQ to SQL 類別 （O-R 設計工具）](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
