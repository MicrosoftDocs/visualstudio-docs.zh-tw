---
title: C# IntelliSense
description: '瞭解在撰寫 c # 專案的程式碼時，可以使用的一些 IntelliSense 功能。'
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3156b1236a130478d83fe82c8fa462a1144a8e6a
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2021
ms.locfileid: "111351951"
---
# <a name="c-intellisense"></a>C# IntelliSense

在編輯器中撰寫程式碼，以及在即時 [模式](../ide/reference/immediate-window.md) 命令視窗中進行偵錯工具時，都可以使用 c # IntelliSense。

## <a name="completion-lists"></a>自動完成清單

C# 中的 IntelliSense 完成清單包含來自清單成員和自動完成文字等的語彙基元。 它可以讓您快速存取：

- 類型或命名空間的成員

- 變數、命令及函式名稱

- 程式碼片段

- 語言關鍵字

- 擴充方法

C# 中的自動完成清單也十分聰明，可以篩選掉不相關的語彙基元，並根據內容預先選取語彙基元。 如需詳細資訊，請參閱篩選後的 [完成清單](#filtered-completion-lists)。

### <a name="code-snippets-in-completion-lists"></a>完成清單中的程式碼片段

C# 完成清單包含程式碼片段，可以協助您在程式中輕鬆地插入預先定義的程式碼主體。 完成清單中顯示為程式碼片段[捷徑文字](../ide/code-snippets-schema-reference.md#shortcut-element)的程式碼片段。 如需 c # 中預設可用程式碼片段的詳細資訊，請參閱 [c # 程式碼片段](../ide/visual-csharp-code-snippets.md)。

### <a name="language-keywords-in-completion-lists"></a>完成清單中的語言關鍵字

C# 的完成清單也包含語言關鍵字。 如需 c # 語言關鍵字的詳細資訊，請參閱 [c # 關鍵字](/dotnet/csharp/language-reference/keywords/index)。

### <a name="extension-methods-in-completion-lists"></a>完成清單中的擴充方法

C# 的完成清單包含範圍內的擴充方法。

> [!NOTE]
> 完成清單不會顯示 <xref:System.String> 物件的所有擴充方法 。

擴充方法與執行個體方法使用不同的圖示。 如需清單圖示參考指南，請參閱[類別檢視和物件瀏覽器圖示](../ide/class-view-and-object-browser-icons.md)。 當同名的執行個體方法與擴充方法都在範圍中時，完成清單會顯示擴充方法圖示。

### <a name="filtered-completion-lists"></a>篩選後的自動完成清單

IntelliSense 會利用篩選條件，將不必要的成員從完成名單中移除。 C# 會篩選針對下列項目所顯示的完成清單：

- **介面與基底類別**：在類別宣告基底和介面清單與條件約束清單中，IntelliSense 都會自動從介面和基底類別的完成清單移除項目。 例如，列舉不會出現在基底類別的完成清單中，因為列舉不能使用於基底類別。 基底類別的完成清單只包含介面和命名空間。 如果您在清單中選取一個項目，然後輸入一個逗號，IntelliSense 會將基底類別從清單中移除，因為 C# 不支援多重繼承。 相同的行為也會發生在條件約束子句。

- **屬性**：當您將屬性套用至類型時，完成清單會經過篩選，讓清單只包括從含有這些類型的命名空間繼承而來之類型，例如 <xref:System.Attribute>。

- **Catch 子句**

- **物件初始設定式**：只有能夠初始化的成員會出現在完成清單中。

- **new 關鍵字**：當您鍵入 `new` 然後按下 **空格鍵** 時，完成清單隨即出現。 清單會根據您的程式碼內容，自動選取一個項目。 例如，完成清單中的項目會針對宣告及方法中的 return 陳述式自動選取項目。

- **enum 關鍵字**：當您在列舉指派的等號之後按 **空格鍵** 時，完成清單隨即出現。 清單會根據您的程式碼內容，自動選取一個項目。 例如，當您鍵入關鍵字 return 並執行宣告時，就會自動選取完成清單中的項目。

- **as 和 is 運算子**：當您鍵入 `as` 或 `is` 關鍵字後按 **空格鍵**，即會自動顯示篩選後的完成清單。

- **事件**：當您輸入關鍵字時 `event` ，完成清單只會包含委派類型。

- **參數說明** 會自動排序到符合您所輸入之參數的第一個方法多載。 如有多個方法多載，您可以使用向上鍵與向下鍵巡覽至清單中下一個可能的多載。

### <a name="most-recently-used-members"></a>最近使用的成員

IntelliSense 會記住您最近在 [[列出成員]](../ide/using-intellisense.md) 快顯方塊中選取的成員，自動完成物件名稱。 下次您使用 **成員清單** 時，最近使用的成員會顯示在頂端。 會在每個 Visual Studio 工作階段之間，清除最近使用過的成員記錄。

### <a name="override"></a>override

當您鍵入 [override](/dotnet/csharp/language-reference/keywords/override)，然後按下 **空格鍵** 時，IntelliSense 即會在快顯清單方塊中顯示所有您可以覆寫的有效基底類別成員。 在 `override` 之後輸入方法的傳回型別，可提示 IntelliSense 僅顯示會傳回相同型別的方法。 當 IntelliSense 找不到任何相符項目時，它會顯示所有基底類別成員。

### <a name="ai-enhanced-intellisense"></a>由 AI 增強的 IntelliSense

[Visual Studio IntelliCode](/visualstudio/intellicode/intellicode-visual-studio) 提供由人工智慧增強的 IntelliSense 自動完成清單。 IntelliCode 可預測要使用哪個最可能正確的 API，而不僅僅是按字母順序排列來呈現成員清單。 它會使用您目前的程式碼內容和模式，以提供動態清單。

## <a name="automatic-code-generation"></a>自動產生程式碼

### <a name="add-using"></a>加入 using

**加入 using** IntelliSense 作業會自動將必要的 `using` 指示詞新增至程式碼檔案。 此功能可讓您專注在自己所撰寫的程式碼上，而不需要將焦點轉移到其他部分的程式碼。

若要起始 **Add using** 作業，請將游標放在無法解析的類型參考上。 例如，當您建立主控台應用程式，然後將 `XmlReader` 新增至 `Main` 方法主體時，該行程式碼就會出現紅色波浪線，因為無法解析類型參考。 您可以接著透過 [快速動作] 叫用 **新增 using**。 只有當游標停在未繫結的類型上時，才會顯示 [快速動作]。

![新增 using，快速動作展開的影像](../ide/media/addusing-quickaction.png)

按一下錯誤燈泡圖示，然後選擇 [using System.Xml;] 自動新增 using 指示詞。

### <a name="add-missing-using-directives-on-paste"></a>貼上時新增缺少的 Using 指示詞

當您將型別貼到程式碼檔案時，IntelliSense 可以自動將遺漏的指示詞新增 `using` 至您的程式碼。 這項功能可讓您在將類型貼到檔案時，將新增遺漏 using 指示詞的工作自動化，以節省您的時間。 在 [**工具**  >  **選項**  >  **文字編輯器** c #] 或 [基本] Advanced 中啟用這項功能  >     >   ，並選取 [**貼上時加入遺漏 using** 指示詞

### <a name="remove-and-sort-usings"></a>移除和排序 Using

[移除和排序 Using] 選項會排序並移除 `using` 和 `extern` 宣告，但不變更原始程式碼的行為。 不必要且缺乏組織的 `using` 指示詞會使原始程式碼隨著時間而變得繁雜難以閱讀。 [移除和排序 Using] 選項可移除未使用的 `using` 指示詞來精簡原始程式碼，並加以排序來改善可讀性。 在 [編輯] 功能表上，選擇 [IntelliSense]，然後選擇 [組合管理 Using]。

### <a name="implement-interface"></a>實作介面

在程式碼編輯器中工作時，IntelliSense 提供可協助您執行 [介面](/dotnet/csharp/language-reference/keywords/interface) 的選項。 一般來說，若要正確地實作介面，必須為類別中介面的每位成員建立方法宣告。 使用 IntelliSense，在類別宣告中輸入介面名稱後，就會顯示 [ **快速動作** ] 燈泡。 您可利用燈泡，選擇要使用明確或隱含命名的方式進行自動實作介面。 在明確命名下，方法宣告會帶有介面的名稱。 在隱含命名下，方法宣告不會指出其所屬介面。 明確命名的介面方法只可透過介面執行個體而不是透過類別執行個體加以存取。 如需詳細資訊，請參閱 [明確介面實行](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)。

實作介面將會產生滿足介面所需之方法虛設常式的數目下限。 如果基底類別實作部分的介面，則不會重新產生那些虛設常式。

### <a name="implement-abstract-base-class"></a>實作抽象基底類別

在使用程式碼編輯器時，IntelliSense 提供您可自動實作抽象基底類別成員的選項。 一般而言，實作抽象基底類別的成員需要針對衍生類別中抽象基底類別的每個方法建立新的方法定義。 使用 IntelliSense，在類別宣告中輸入抽象基類的名稱後，就會顯示 **快速動作** 燈泡。 燈泡提供您自動實作基底類別方法的選項。

由「 **執行抽象基類** 」功能所產生的方法存根，會由 *MethodStub* 檔案中所定義的程式碼片段進行模型化。 程式碼片段是可以修改的。 如需詳細資訊，請參閱[逐步解說：建立程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)。

### <a name="generate-from-usage"></a>使用時產生

[使用時產生] 功能可讓您直接使用類別和成員，而不需要先行定義。 您可以為任何想要使用但尚未定義的類別、建構函式、方法、屬性、欄位或列舉，產生虛設常式。 您可以產生新類型和成員，不用離開目前在程式碼中的位置。 這可將對工作流程的干擾降至最低。

每個未定義的識別碼下都會顯示紅色波浪底線。 當您將滑鼠指標放在識別碼時，工具提示中就會出現錯誤訊息。 若要顯示適當的選項，您可以使用下列其中一項程序：

- 按一下未定義的識別碼。 [快速動作] 錯誤燈泡會出現在識別碼下。 按一下錯誤燈泡。

- 按一下未定義的識別碼，然後按下 **Ctrl** + **。**  (**Ctrl** + 句號) 。

- 以滑鼠右鍵按一下未定義的識別碼，然後按一下 [快速動作及重構]。

顯示的選項包括：

- **產生屬性**

- **產生欄位**

- **產生方法**

- **產生類別**

- **產生新的類型** (針對類別、結構、介面或列舉)

## <a name="generate-event-handlers"></a>產生事件處理常式

在程式碼編輯器中，IntelliSense 可協助您將方法 (事件處理常式) 連結到事件欄位。

當您在 .cs 檔案的 `+=` 事件欄位後面輸入運算子時，IntelliSense 會提示您按下 **tab** 鍵的選項。 這會插入委派的新執行個體，指向處理事件的方法。

![按鈕自動連結](../ide/media/vxautohookup.gif)

如果您按下 **tab** 鍵，IntelliSense 會自動為您完成語句，並在程式碼編輯器中將事件處理常式參考顯示為選取的文字。 為了完成自動事件連結，IntelliSense 會提示您再次按下 **tab** 鍵，為事件處理常式建立空白的存根。

![產生事件處理常式](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> 如果 IntelliSense 建立的新委派，參考的是現有的事件處理常式，IntelliSense 就會在工具提示中傳達這項資訊。 接著您就可以修改此參考，程式碼編輯器中已選取該文字。 否則，自動事件連結即於此刻完成。

如果您按下 **tab** 鍵，IntelliSense 會以正確的簽章來取代方法，並將游標放在事件處理常式的主體中。

> [!NOTE]
> 使用 [檢視] 功能表上的 [向後巡覽] 命令 (**Ctrl**+**-**)，返回事件連結陳述式。

## <a name="see-also"></a>另請參閱

- [使用 IntelliSense](../ide/using-intellisense.md)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
