---
title: 如何使用 XML 程式碼片段
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e72c5ef5d5c33c46a9f09eb604d0a2e40cf9a6e7
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815912"
---
# <a name="how-to-use-xml-snippets"></a>如何：使用 XML 片段

您可以使用 XML 編輯器快捷方式功能表上的下列兩個命令來叫用 XML 程式碼片段。 [**插入程式碼片段**] 命令會在游標位置插入 XML 程式碼片段。 [**環繞于**] 命令會將 XML 程式碼片段包裝在選取的文字周圍。 每個 XML 片段都具有指定的片段型別。 程式碼片段類型會使用 [**插入程式碼片段** **] 命令、[範圍**語句] 命令或兩者，來判斷程式碼片段是否可供使用。

將 XML 片段加入編輯器後，片段中所有可編輯的欄位均會以黃色反白顯示，且游標位於第一個可編輯欄位上。

## <a name="insert-snippet"></a>插入片段

下列程式說明如何存取 [**插入程式碼片段**] 命令。

> [!NOTE]
> [**插入程式碼片段**] 命令也可以透過鍵盤快速鍵（**ctrl** + **K**、 **ctrl** + **X**）來取得。

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>透過捷徑功能表插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 以滑鼠右鍵按一下並選取 [**插入程式碼片段**]。

   會顯示可用 XML 片段的清單。

3. 使用滑鼠選取清單中的程式碼片段，或輸入程式碼片段的名稱，然後按**tab**或**enter**鍵。

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>使用 IntelliSense 功能表插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 從 [**編輯**] 功能表，指向 [ **IntelliSense**]，然後選取 [**插入程式碼片段**]。

   會顯示可用 XML 片段的清單。

3. 使用滑鼠或輸入程式碼片段的名稱，然後按**tab**或**enter**鍵，從清單中選取程式碼片段。

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>若要透過 IntelliSense 自動完成文字清單插入程式碼片段

1. 將游標置於您要插入 XML 片段的位置。

2. 開始鍵入您想要加入檔案的 XML 片段。 如果自動完成已開啟，則會顯示 IntelliSense 自動完成清單。 如果沒有出現，請按**Ctrl** + **空格鍵**來啟動它。

3. 從自動完成清單中選取 XML 片段。

4. 按**tab**、 **tab**以叫用 XML 片段。

> [!NOTE]
> 有時可能無法叫用 XML 片段。 例如，如果您嘗試在 `xs:complexType` 節點內插入 `xs:element` 項目，則編輯器不會產生 XML 片段。 在 `xs:complexType` 節點內使用 `xs:element` 項目時，因為沒有必要的屬性或項目子系，所以編輯器並無任何要插入的資料。

### <a name="to-insert-snippets-using-the-shortcut-name"></a>使用捷徑名稱插入片段

1. 將游標置於您要插入 XML 片段的位置。

2. 在編輯器窗格中鍵入 `<`。

3. 按下**Esc**鍵以關閉 [IntelliSense 自動完成字組] 清單。

4. 輸入程式碼片段的快捷方式名稱，然後按**tab**鍵來叫用 XML 片段。

## <a name="surround-with"></a>以此環繞

下列程式說明如何**存取 [範圍**語句] 命令。

> [!NOTE]
> [範圍語句 **] 命令也**可以透過鍵盤快速鍵（**ctrl** + **K**、 **ctrl** + **S**）來取得。

### <a name="to-use-surround-with-from-the-context-menu"></a>若要從內容功能表使用範圍語句

1. 選取要在 XML 編輯器中環繞的文字。

2. 按一下滑鼠**右鍵，然後選取 [** 範圍語句]。

   會顯示可用以此環繞 XML 片段的清單。

3. 使用滑鼠選取清單中的程式碼片段，或輸入程式碼片段的名稱，然後按**tab**或**enter**鍵。

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>若要從 IntelliSense 功能表使用範圍語句

1. 選取要在 XML 編輯器中環繞的文字。

2. 從 [**編輯**] 功能表，指向 [ **IntelliSense**]，然後選取 [**以範圍括住**]。

   會顯示可用以此環繞 XML 片段的清單。

3. 使用滑鼠選取清單中的程式碼片段，或輸入程式碼片段的名稱，然後按**tab**或**enter**鍵。

## <a name="use-xml-snippets"></a>使用 XML 程式碼片段

一旦選擇了 XML 片段，程式碼片段的文字便會自動插入游標位置。 會反白顯示片段中任何可編輯的欄位，並自動選取第一個可編輯的欄位。 目前選取的欄位為 boxed。

選取欄位後，您可以為該欄位鍵入新值。 按**tab**鍵會迴圈顯示程式碼片段的可編輯欄位;按下**Shift** + **Tab**會以相反順序迴圈。 按一下欄位便會將游標置於該欄位中，而按兩下欄位便會選取它。 反白顯示欄位後，可能會顯示提供欄位說明的工具提示。

只有給定欄位的第一個執行個體才是可編輯的。 反白顯示該欄位時，會為欄位之其他執行個體加上外框。 當您變更可編輯欄位的值時，該片段中任何位置所使用的這個欄位均會變更。

按**enter**或**Esc**可取消欄位編輯，並將編輯器恢復正常。

您可以在 [**選項**] 對話方塊的 [字型**和色彩**] 窗格中修改**程式碼片段欄位**設定，以變更可編輯之程式碼片段欄位的預設色彩。 如需詳細資訊，請參閱[如何：變更編輯器中的字型和色彩](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)。

## <a name="see-also"></a>另請參閱

- [XML 程式碼片段](../xml-tools/xml-snippets.md)
- [如何：從 XML 架構產生 XML 程式碼片段](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [如何：建立 XML 片段](../xml-tools/how-to-create-xml-snippets.md)
