---
title: "產生 XML 文件註解-產生程式碼 (C#) |Microsoft 文件"
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
ms.openlocfilehash: f1c1dfb69c12eb183ecf3435346a543488ebe0e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="generate-xml-documentation-comments-in-c"></a>在 C# 中產生 XML 文件註解 #
**項目：**可讓您立即產生 XML 文件的選取項目所需的基底。 

**當：**您想要建立 XML 文件註解，以便之後處理 Sandcastle 這類文件工具。

**原因：**您可以手動整個註解區塊自行建立，不過這將會節省時間，並改善正確性所產生的基底範本和其他項目。 

**如何：**

1. 將文字游標在您想要記錄，例如方法的項目。

   ![文件的方法](media/doc_highlight.png)

1. 接著，輸入 **///**  （3 開始斜線） 將會視需要自動建立基底範本和其他項目。  例如，當標記為註解的方法，它會產生**\<摘要\>**標記以及 **\<param\>** 是每個參數標記傳遞至方法，和**\<傳回\>**標記加入至方法的傳回的文件。

   ![範本](media/doc_preview.png)

1. 完成註解，並新增任何額外的資訊，您認為是必要的。

   ![已完成的註解](media/doc_result.png)

## <a name="see-also"></a>請參閱
[程式碼產生 (C#)](../code-generation-csharp.md)  
[XML 文件註解 (C# 程式設計手冊)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
