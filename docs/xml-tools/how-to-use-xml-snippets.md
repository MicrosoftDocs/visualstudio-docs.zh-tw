---
title: 如何使用 XML 程式碼片段
description: 瞭解如何使用 XML 編輯器中的命令來插入 XML 程式碼片段，或在選取的文字周圍包裝 XML 程式碼片段。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bebca3a27d11015388e45ff6839f446506e716c
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970603"
---
# <a name="how-to-use-xml-snippets"></a>如何：使用 XML 程式碼片段

您可以使用 XML 編輯器快捷方式功能表上的下列兩個命令來叫用 XML 片段。 [ **插入程式碼片段** ] 命令會在游標位置插入 XML 程式碼片段。 「範圍語句」命令會將所選文字周圍的 XML 程式碼片段包裝 **起來** 。 每個 XML 片段都具有指定的片段型別。 程式碼片段類型會判斷程式碼片段是否可用於 **插入程式碼片段** 命令、 **環繞 with** 命令或兩者。

將 XML 片段加入編輯器後，片段中所有可編輯的欄位均會以黃色反白顯示，且游標位於第一個可編輯欄位上。

## <a name="insert-snippet"></a>插入片段

下列程式說明如何存取 [ **插入程式碼片段** ] 命令。

> [!NOTE]
> [**插入程式碼片段**] 命令也可以透過鍵盤快速鍵 (**Ctrl** + **K**，然後按 **ctrl** + **X**) 。

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>透過捷徑功能表插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 以滑鼠右鍵按一下並選取 [ **插入程式碼片段**]。

   會顯示可用 XML 片段的清單。

3. 使用滑鼠從清單中選取程式碼片段，或輸入程式碼片段的名稱並按 **tab** 鍵或 **enter** 鍵。

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>使用 IntelliSense 功能表插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 從 [ **編輯** ] 功能表，指向 [ **IntelliSense**]，然後選取 [ **插入程式碼片段**]。

   會顯示可用 XML 片段的清單。

3. 使用滑鼠，或鍵入程式碼片段的名稱並按 **tab** 鍵或 **enter** 鍵，從清單中選取程式碼片段。

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>若要透過 IntelliSense 完成字組插入程式碼片段

1. 將游標置於您要插入 XML 片段的位置。

2. 開始鍵入您想要加入檔案的 XML 片段。 如果自動完成已開啟，則會顯示 IntelliSense 自動完成清單。 如果沒有出現，請按下 **Ctrl** + **空格鍵** 來啟用它。

3. 從自動完成清單中選取 XML 片段。

4. 按 **tab** 鍵 **，以** 叫用 XML 片段。

> [!NOTE]
> 有時可能無法叫用 XML 片段。 例如，如果您嘗試在 `xs:complexType` 節點內插入 `xs:element` 項目，則編輯器不會產生 XML 片段。 在 `xs:complexType` 節點內使用 `xs:element` 項目時，因為沒有必要的屬性或項目子系，所以編輯器並無任何要插入的資料。

### <a name="to-insert-snippets-using-the-shortcut-name"></a>使用捷徑名稱插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 在編輯器窗格中鍵入 `<`。

3. 按下 **Esc** 鍵以關閉 IntelliSense 完成字組清單。

4. 輸入程式碼片段的快捷方式名稱，然後按下 **tab** 以叫用 XML 片段。

## <a name="surround-with"></a>以此環繞

下列程式說明如何存取 [ **以環繞** ] 命令。

> [!NOTE]
> 您也可以透過鍵盤快速鍵 (**ctrl** **Surround With** + **K**，然後按 **ctrl** + **S**) 來使用 [環繞于] 命令。

### <a name="to-use-surround-with-from-the-context-menu"></a>若要從內容功能表使用範圍語句

1. 在 XML 編輯器中選取要環繞的文字。

2. 以滑鼠右鍵按一下並選取 [ **環繞于**]。

   會顯示可用以此環繞 XML 片段的清單。

3. 使用滑鼠從清單中選取程式碼片段，或輸入程式碼片段的名稱並按 **tab** 鍵或 **enter** 鍵。

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>從 IntelliSense 功能表使用範圍語句

1. 在 XML 編輯器中選取要環繞的文字。

2. 從 [ **編輯** ] 功能表，指向 [ **IntelliSense**]，然後 **選取 [** 範圍語句]。

   會顯示可用以此環繞 XML 片段的清單。

3. 使用滑鼠從清單中選取程式碼片段，或輸入程式碼片段的名稱並按 **tab** 鍵或 **enter** 鍵。

## <a name="use-xml-snippets"></a>使用 XML 程式碼片段

一旦選擇了 XML 片段，程式碼片段的文字便會自動插入游標位置。 會反白顯示片段中任何可編輯的欄位，並自動選取第一個可編輯的欄位。 目前選取的欄位為 boxed。

選取欄位後，您可以為該欄位鍵入新值。 按 **tab** 鍵可編輯程式碼片段的可編輯欄位;按下 **Shift** + **鍵** 會以反向順序逐一迴圈。 按一下欄位便會將游標置於該欄位中，而按兩下欄位便會選取它。 反白顯示欄位後，可能會顯示提供欄位說明的工具提示。

只有給定欄位的第一個執行個體才是可編輯的。 反白顯示該欄位時，會為欄位之其他執行個體加上外框。 當您變更可編輯欄位的值時，該片段中任何位置所使用的這個欄位均會變更。

按 **enter** 或 **Esc** 可取消欄位編輯，並將編輯器傳回一般。

您可以在 [**選項**] 對話方塊的 [字型 **和色彩**] 窗格中修改 **程式碼片段欄位** 設定，以變更可編輯的程式碼片段欄位預設色彩。 如需詳細資訊，請參閱 [如何：在編輯器中變更字型和色彩](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)。

## <a name="see-also"></a>另請參閱

- [XML 片段](../xml-tools/xml-snippets.md)
- [如何：從 XML 架構產生 XML 片段](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [如何：建立 XML 片段](../xml-tools/how-to-create-xml-snippets.md)
