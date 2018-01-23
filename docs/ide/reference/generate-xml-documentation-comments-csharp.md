---
title: "產生 XML 文件註解 - 程式碼產生 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b0a0ec1db54f57e14ddd412248f7a396336fe009
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="generate-xml-documentation-comments-in-c"></a>使用 C# 來產生 XML 文件註解 #
**功能：**讓您立即產生記載所選元素所需的基底 XML。 

**時機：**您想要建立「XML 文件註解」以在之後由文件工具 (例如 Sandcastle) 進行處理。

**原因：**您可以自行手動建立整個註解區塊，不過，此功能將可藉由產生基底範本和額外元素，來節省時間及提升準確性。 

**做法：**

1. 將文字游標放在您想要記載的元素 (例如方法) 上方。

   ![要記載的方法](media/doc-highlight-cs.png)

1. 接著，輸入 **///** (3 條正斜線)，這會自動建立基底範本和任何必要的額外元素。  例如，為方法加上註解時，會為傳遞給方法的每個參數產生 **\<summary\>** 標記及 **\<param\>** 標記，還會產生 **\<returns\>** 標記來記載方法所傳回的內容。

   ![範本](media/doc-preview-cs.png)

1. 完成註解並新增任何您認為必要的額外資訊。

   ![已完成的註解](media/doc-result-cs.png)

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)  
[XML 文件註解 (C# 程式設計手冊)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
