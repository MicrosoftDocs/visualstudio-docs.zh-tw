---
title: 如何使用 XML 片段
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d892ba202a73560568bdb6c43427a8ee0f7c1aee
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913622"
---
# <a name="how-to-use-xml-snippets"></a>HOW TO：使用 XML 片段

您可以使用 XML 編輯器捷徑功能表上的下列兩個命令叫用 XML 片段。 **插入程式碼片段**命令會將 XML 程式碼片段插入游標位置。 **環繞**命令會以 XML 片段環繞選定文字。 每個 XML 片段都具有指定的片段型別。 程式碼片段類型可讓您決定是否可與程式碼片段**插入程式碼片段**命令**環繞**命令，或兩者。

將 XML 片段加入編輯器後，片段中所有可編輯的欄位均會以黃色反白顯示，且游標位於第一個可編輯欄位上。

## <a name="insert-snippet"></a>插入片段

下列程序說明如何存取**插入程式碼片段**命令。

> [!NOTE]
> **插入程式碼片段**命令也會提供透過鍵盤快速鍵 (**Ctrl**+**K**，然後**Ctrl** +**X**)。

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>透過捷徑功能表插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 以滑鼠右鍵按一下並選取**插入程式碼片段**。

   會顯示可用 XML 片段的清單。

3. 選取程式碼片段，從清單中使用滑鼠，或輸入名稱的程式碼片段並按** 索引標籤**或是**Enter**。

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>使用 IntelliSense 功能表插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 從**編輯**功能表上，指向**IntelliSense**，然後選取**插入程式碼片段**。

   會顯示可用 XML 片段的清單。

3. 選取程式碼片段，從清單中使用滑鼠，或輸入名稱的程式碼片段並按** 索引標籤**或是**Enter**。

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>若要插入程式碼片段，透過 IntelliSense 自動完成清單

1. 將游標置於您要插入 XML 片段的位置。

2. 開始鍵入您想要加入檔案的 XML 片段。 如果自動完成已開啟，則會顯示 IntelliSense 自動完成清單。 如果沒有出現，請按**Ctrl**+**空間**才能加以啟動。

3. 從自動完成清單中選取 XML 片段。

4. 按下** 索引標籤**， ** 索引標籤**以叫用 XML 片段。

> [!NOTE]
> 有時可能無法叫用 XML 片段。 例如，如果您嘗試在 `xs:complexType` 節點內插入 `xs:element` 項目，則編輯器不會產生 XML 片段。 在 `xs:complexType` 節點內使用 `xs:element` 項目時，因為沒有必要的屬性或項目子系，所以編輯器並無任何要插入的資料。

### <a name="to-insert-snippets-using-the-shortcut-name"></a>使用捷徑名稱插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 在編輯器窗格中鍵入 `<`。

3. 按下**Esc**關閉 IntelliSense 自動完成文字清單。

4. 輸入捷徑名稱的程式碼片段，然後按** 索引標籤**以叫用 XML 片段。

## <a name="surround-with"></a>以此環繞

下列程序說明如何存取**環繞**命令。

> [!NOTE]
> **環繞**命令也會提供透過鍵盤快速鍵 (**Ctrl**+**K**，然後**Ctrl** +**S**)。

### <a name="to-use-surround-with-from-the-context-menu"></a>若要從內容功能表使用範圍陳述式

1. 在 [XML 編輯器] 中選取要環繞的文字。

2. 以滑鼠右鍵按一下並選取**環繞**。

   會顯示可用以此環繞 XML 片段的清單。

3. 選取程式碼片段，從清單中使用滑鼠，或輸入名稱的程式碼片段並按** 索引標籤**或是**Enter**。

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>若要從 IntelliSense 功能表使用範圍陳述式

1. 在 [XML 編輯器] 中選取要環繞的文字。

2. 從**編輯**功能表上，指向**IntelliSense**，然後選取**環繞**。

   會顯示可用以此環繞 XML 片段的清單。

3. 選取程式碼片段，從清單中使用滑鼠，或輸入名稱的程式碼片段並按** 索引標籤**或是**Enter**。

## <a name="use-xml-snippets"></a>使用 XML 片段

一旦選擇了 XML 片段，程式碼片段的文字便會自動插入游標位置。 會反白顯示片段中任何可編輯的欄位，並自動選取第一個可編輯的欄位。 目前選取的欄位為 boxed。

選取欄位後，您可以為該欄位鍵入新值。 按下** 索引標籤**循環的程式碼片段可編輯的欄位; 按下**Shift**+**索引標籤**以反向順序逐一循環。 按一下欄位便會將游標置於該欄位中，而按兩下欄位便會選取它。 反白顯示欄位後，可能會顯示提供欄位說明的工具提示。

只有給定欄位的第一個執行個體才是可編輯的。 反白顯示該欄位時，會為欄位之其他執行個體加上外框。 當您變更可編輯欄位的值時，該片段中任何位置所使用的這個欄位均會變更。

按下**Enter**或是**Esc**取消欄位編輯，並將編輯器返回正常狀態。

可以變更可編輯的程式碼片段欄位的預設色彩，藉由修改**程式碼片段欄位**中設定**字型和色彩**窗格**選項** 對話方塊。 如需詳細資訊，請參閱[＜How to：變更編輯器中的字型和色彩](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)。

## <a name="see-also"></a>另請參閱

- [XML 程式碼片段](../xml-tools/xml-snippets.md)
- [如何：從 XML 結構描述產生 XML 片段](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [如何：建立 XML 片段](../xml-tools/how-to-create-xml-snippets.md)