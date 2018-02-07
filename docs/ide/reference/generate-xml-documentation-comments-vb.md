---
title: "產生 Visual Basic 的 XML 文件註解 | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2f421553657dfafb265140e44e38a2c7722a7303
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="generate-xml-documentation-comments-in-visual-basic"></a>使用 Visual Basic 來產生 XML 文件註解

**功能：**讓您立即產生記載所選元素所需的基底 XML。 

**時機：**您想要建立「XML 文件註解」以在之後由文件工具 (例如 Sandcastle) 進行處理。

**原因：**您可以自行手動建立整個註解區塊，不過，此功能將可藉由產生基底範本和額外元素，來節省時間及提升準確性。 

**做法：**

1. 將文字游標放在您想要記載的元素 (例如方法) 上方。

   ![要記載的方法](media/doc-highlight-vb.png)

1. 接著，輸入 **'''** (3 個單引號)，這會自動建立基底範本和任何必要的額外元素。  例如，為方法加上註解時，會為傳遞給方法的每個參數產生 **\<summary\>** 標記及 **\<param\>** 標記，還會產生 **\<returns\>** 標記來記載方法所傳回的內容。

   ![範本](media/doc-preview-vb.png)

1. 完成註解並新增任何您認為必要的額外資訊。

   ![已完成的註解](media/doc-result-vb.png)

## <a name="see-also"></a>另請參閱

[使用 XML 在程式碼中加入文件 (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)  
[程式碼產生](../code-generation-in-visual-studio.md)