---
title: 如何：搭配使用中斷點與 XSLT |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656300"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>HOW TO：搭配使用中斷點與 XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可在 XSLT 樣式表或 XML 來源文件中設定中斷點。 如果您在標記上設定了中斷點，則在開始執行時，中斷點會移至下一個具有原始程式行資訊的陳述式 (Statement)。

 如需詳細資訊，請參閱[偵錯工具基本概念：中斷點](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)。

## <a name="set-a-breakpoint-in-a-style-sheet"></a>在樣式表中設定中斷點
 中斷點可在 XSLT 樣式表的開始標記、結束標記及文字節點上設定。 中斷點也可以在指令碼區塊的程式碼上設定。

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>在樣式表中設定中斷點

1. 在 XML 編輯器中開啟樣式表。

2. 將游標放在中斷點位置，以滑鼠右鍵按一下，指向 [**中斷點**]，然後按一下 [**插入中斷點**]。

3. 在 [檔案屬性] 視窗的 [**輸入**] 欄位上，按一下 [流覽] 按鈕（ **...** ）。

4. 找出 XML 來源文件，然後按一下 [**開啟**]。

     這會設定用於 XSLT 轉換的來源文件檔案。

5. 按一下 [XML 編輯器] 工具列上的 [ **DEBUG XSL** ] 按鈕。

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>在 XML 來源文件中設定中斷點
 中斷點可以在 XML 來源文件的項目、屬性、命名空間節點、註解、處理指示與文字節點上設定。 您無法在文件節點或從父項目繼承的命名空間節點上設定中斷點。

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>在 XML 來源文件中設定中斷點

1. 在 XML 編輯器中開啟 XML 文件。

2. 將游標放在中斷點位置，以滑鼠右鍵按一下，指向 [**中斷點**]，然後按一下 [**插入中斷點**]。

3. 在 [檔案屬性] 視窗的 [**樣式**表單] 欄位上，按一下 [流覽] 按鈕（ **...** ）。

4. 找出 XML 來源文件，然後按一下 [**開啟**]。

     這會設定用於 XSLT 轉換的來源文件檔案。

5. 按一下 [XML 編輯器] 工具列上的 [ **DEBUG XSL** ] 按鈕。

## <a name="see-also"></a>請參閱
 [逐步解說：偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
