---
title: 如何：使用 XML 片段 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4998fbc530cf4350f4a64b0fd527e0764eafce27
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656268"
---
# <a name="how-to-use-xml-snippets"></a>HOW TO：使用 XML 片段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 XML 編輯器捷徑功能表上的下列兩個命令叫用 XML 片段。 [**插入程式碼片段**] 命令會在游標位置插入 XML 程式碼片段。 [**環繞于**] 命令會將 XML 程式碼片段包裝在選取的文字周圍。 每個 XML 片段都具有指定的片段型別。 程式碼片段類型會使用 [**插入程式碼片段** **] 命令、[範圍**語句] 命令或兩者，來判斷程式碼片段是否可供使用。

 將 XML 片段加入編輯器後，片段中所有可編輯的欄位均會以黃色反白顯示，且游標位於第一個可編輯欄位上。

## <a name="insert-snippet"></a>插入片段
 下列程式說明如何存取 [**插入程式碼片段**] 命令。

> [!NOTE]
> 也可以透過鍵盤快速鍵（CTRL + K、CTRL + X）來使用 [**插入程式碼片段**] 命令。

#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>透過捷徑功能表插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 以滑鼠右鍵按一下並選取 [**插入程式碼片段**]。

     會顯示可用 XML 片段的清單。

3. 使用滑鼠，或藉由鍵入片段名稱並按 TAB 鍵或 ENTER 鍵，從清單中選取片段。

#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>使用 IntelliSense 功能表插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 從 [**編輯**] 功能表，指向 [ **IntelliSense**]，然後選取 [**插入程式碼片段**]。

     會顯示可用 XML 片段的清單。

3. 使用滑鼠，或藉由鍵入片段名稱並按 TAB 鍵或 ENTER 鍵，從清單中選取片段。

#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>透過 IntelliSense 自動完成清單插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 開始鍵入您想要加入檔案的 XML 片段。 如果自動完成已開啟，則會顯示 IntelliSense 自動完成清單。 如果清單未出現，請按 CTRL+SPACEBAR 啟動它。

3. 從自動完成清單中選取 XML 片段。

4. 按 TAB 鍵，以叫用 XML 片段。

> [!NOTE]
> 有時可能無法叫用 XML 片段。 例如，如果您嘗試在 `xs:complexType` 節點內插入 `xs:element` 項目，則編輯器不會產生 XML 片段。 在 `xs:complexType` 節點內使用 `xs:element` 項目時，因為沒有必要的屬性或項目子系，所以編輯器並無任何要插入的資料。

#### <a name="to-insert-snippets-using-the-shortcut-name"></a>使用捷徑名稱插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 在編輯器窗格中鍵入 `<`。

3. 按 ESC 鍵關閉 IntelliSense 自動完成字組清單。

4. 鍵入片段的捷徑名稱，並按 TAB 鍵以叫用 XML 片段。

## <a name="surround-with"></a>以此環繞
 下列程式說明如何**存取 [範圍**語句] 命令。

> [!NOTE]
> [範圍語句 **] 命令也**可以透過鍵盤快速鍵（Ctrl + K、Ctrl + S）來取得。

#### <a name="to-use-surround-with-from-the-context-menu"></a>透過操作功能表使用以此環繞

1. 在 [XML 編輯器] 中選取要環繞的文字。

2. 按一下滑鼠**右鍵，然後選取 [** 範圍語句]。

     會顯示可用以此環繞 XML 片段的清單。

3. 使用滑鼠，或藉由鍵入片段名稱並按 TAB 鍵或 ENTER 鍵，從清單中選取片段。

#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>透過 Intellisense 功能表使用以此環繞

1. 在 [XML 編輯器] 中選取要環繞的文字。

2. 從 [**編輯**] 功能表，指向 [ **IntelliSense**]，然後選取 [**以範圍括住**]。

     會顯示可用以此環繞 XML 片段的清單。

3. 使用滑鼠，或藉由鍵入片段名稱並按 TAB 鍵或 ENTER 鍵，從清單中選取片段。

## <a name="using-xml-snippets"></a>使用 XML 片段
 一旦選擇了 XML 片段，程式碼片段的文字便會自動插入游標位置。 會反白顯示片段中任何可編輯的欄位，並自動選取第一個可編輯的欄位。 目前選取的欄位為 boxed。

 選取欄位後，您可以為該欄位鍵入新值。 按 TAB 鍵轉換片段的可編輯欄位；按 SHIFT+TAB 以相反順序轉換這些欄位。 按一下欄位便會將游標置於該欄位中，而按兩下欄位便會選取它。 反白顯示欄位後，可能會顯示提供欄位說明的工具提示。

 只有給定欄位的第一個執行個體才是可編輯的。 反白顯示該欄位時，會為欄位之其他執行個體加上外框。 當您變更可編輯欄位的值時，該片段中任何位置所使用的這個欄位均會變更。

 按 ENTER 鍵或 ESC 鍵以取消欄位編輯，並將編輯器返回到正常狀態。

 您可以在 [**選項**] 對話方塊的 [字型**和色彩**] 窗格中修改程式碼片段欄位設定，以變更可編輯之程式碼片段欄位的預設色彩。 如需詳細資訊，請參閱[如何：變更編輯器中的字型和色彩](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)。

## <a name="see-also"></a>請參閱
 [Xml 片段](../xml-tools/xml-snippets.md)[如何：從 XML 架構產生 xml 程式碼片段](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)[如何：建立 xml 片段](../xml-tools/how-to-create-xml-snippets.md)
