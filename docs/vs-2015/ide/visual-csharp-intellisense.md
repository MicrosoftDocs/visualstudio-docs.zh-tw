---
title: Visual C# IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [J#]
- Visual C#, IntelliSense
- IntelliSense [C#]
ms.assetid: 79ca304d-dc1e-4dc9-a2a6-7808df2e588e
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8de573e8d5f46988868f18114fdabb07f62690e0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443170"
---
# <a name="visual-c-intellisense"></a>Visual C# IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在編輯器中撰寫程式碼，以及在 [[即時模式]](../ide/reference/immediate-window.md) 命令視窗中偵錯時，有 Visual C# IntelliSense 可供使用。  
  
## <a name="completion-lists"></a>完成清單  
 Visual C# 中的 IntelliSense 完成清單包含來自清單成員和自動完成文字等的語彙基元。 它可以讓您快速存取：  
  
- 類型或命名空間的成員、  
  
- 變數、命令及函式名稱、  
  
- [程式碼片段](#CodeSnippets)、  
  
- [語言關鍵字](#Keywords)、  
  
- [擴充方法](#ExtensionMethods)  
  
  C# 中的完成清單也十分聰明，可以篩選掉不相關的語彙基元，並根據內容預先選取語彙基元。 如需詳細資訊，請參閱 [C# 中已篩選的完成清單](../misc/filtered-completion-lists-in-csharp.md)和 [C# 中預先選取的完成清單項目](../misc/pre-selected-completion-list-items-in-csharp.md)。  
  
### <a name="CodeSnippets"></a> 完成清單中的程式碼片段  
 Visual C# 完成清單包含程式碼片段，可以協助您在程式中輕鬆地插入預先定義的程式碼主體。 在完成清單中，程式碼片段會顯示為片段的 [Shortcut 項目 (IntelliSense 程式碼片段)](http://msdn.microsoft.com/052cc97a-5c70-42f8-b398-4c3adf670cfa)。  如需 Visual C# 中所提供之預設程式碼片段的詳細資訊，請參閱 [Visual C# 程式碼片段](../ide/visual-csharp-code-snippets.md)。  
  
### <a name="Keywords"></a> 完成清單中的語言關鍵字  
 Visual C# 的完成清單也包含語言關鍵字。 如需 C# 語言關鍵字的詳細資訊，請參閱 [C# 關鍵字](http://msdn.microsoft.com/library/e929b0f2-4b92-4d37-8060-23d323b098ad)。  
  
### <a name="ExtensionMethods"></a> 完成清單中的擴充方法  
 Visual C# 的完成清單包含範圍內的擴充方法。  
  
> [!NOTE]
> 完成清單不會顯示 <xref:System.String> 物件的所有擴充方法 。  
  
 擴充方法與執行個體方法使用不同的圖示。 如需清單圖示的清單，請參閱[類別檢視和物件瀏覽器圖示](../ide/class-view-and-object-browser-icons.md)。 當同名的執行個體方法與擴充方法都在範圍中時，完成清單會顯示擴充方法圖示。  
  
### <a name="filtered-completion-lists"></a>篩選後的完成清單  
 IntelliSense 會利用篩選條件，將不必要的成員從完成名單中移除。  
  
 Visual C# 會篩選針對下列項目所顯示的完成清單：  
  
- **介面與基底類別。** 在類別宣告基底和介面清單與條件約束清單中，IntelliSense 都會自動從介面和基底類別的完成清單移除項目。 例如，列舉不會出現在基底類別的完成清單中，因為列舉不能使用於基底類別。 基底類別的完成清單只包含介面和命名空間。 如果您在清單中選取一個項目，然後輸入一個逗號，IntelliSense 會將基底類別從清單中移除，因為 Visual C# 不支援多重繼承。 相同的行為也會發生在條件約束子句。  
  
- **屬性**：當您將屬性套用至類型，完成清單會經過篩選，讓清單只包括從含有這些類型的命名空間繼承而來之類型，例如 <xref:System.Attribute>。  
  
- `as` 及 `is` 運算子。  
  
- **Catch 子句。**  
  
- **物件初始設定式：** 只有能夠初始化的成員會出現在完成清單中。  
  
- **新關鍵字**：當您輸入 `new` 後按空格鍵，完成清單會隨即出現。 清單會根據您的程式碼內容，自動選取一個項目。 例如，完成清單中的項目會針對宣告及方法中的 return 陳述式自動選取項目。  
  
- **為和 is 運算子：** 當您輸入 `as` 或 `is` 關鍵字後按空格鍵，會顯示篩選後的完成清單。  
  
- 事件：當您鍵入 `event` 關鍵字時，完成清單僅會包含委派類型。  
  
- 參數會自動排序到符合您所輸入之參數的第一個方法多載。 如有多個方法多載，您可以使用向上鍵與向下鍵巡覽至清單中下一個可能的多載。  
  
## <a name="most-recently-used-members"></a>最近使用的成員  
 IntelliSense 會記住您最近在 [[列出成員]](../ide/using-intellisense.md) 快顯方塊中選取的成員，自動完成物件名稱。 下次使用 [成員] 清單時，最近使用過的成員就會顯示在頂端。 IDE 會在每個工作階段之間，清除最近使用過的成員記錄。  
  
## <a name="override"></a>override  
 當您鍵入 [override](http://msdn.microsoft.com/library/dd1907a8-acf8-46d3-80b9-c2ca4febada8)，然後按下空格鍵時，IntelliSense 即會在快顯清單方塊中顯示所有您可以覆寫的有效基底類別成員。 在 `override` 之後輸入方法的傳回類型，可提示 IntelliSense 僅顯示會傳回相同類型的方法。 當 IntelliSense 找不到任何相符項目時，它會顯示所有基底類別成員。  
  
## <a name="automatic-code-generation"></a>自動產生程式碼  
  
### <a name="add-using"></a>加入 using  
 加入 using 的 IntelliSense 作業可讓您專注在自己所撰寫的程式碼上，而不需要將焦點轉移到其他部分的程式碼。  
  
 若要起始加入 using 作業，請將游標放在無法解析的類型參考上。 例如，當您建立主控台應用程式，然後將 `XmlTextReader` 新增至 `Main` 方法主體時，智慧標籤將會出現在 `XmlTextReader` 最右邊的字元下方，因為它會顯示為無法解析的類型參考。  
  
 ![新增 using 智慧標籤影像](../ide/media/addusesmart.gif "AddUseSmart")  
  
 若要叫用 [加入 using]，您可以從 [IntelliSense] 功能表中的 [解析] 子功能表或操作功能表加以選取，或透過智慧標籤叫用 [加入 using]。 只有當游標位於未繫結類型的上方或旁邊時，才會顯示智慧標籤。  
  
 ![加入 using，智慧標籤展開的影像](../ide/media/addusesmartexp.gif "AddUseSmartExp")  
  
### <a name="organize-usings"></a>組合管理 Using  
 [組合管理 Using]**`extern` 選項會排序並移除**  和 `using` 宣告，但不變更原始程式碼的行為。 不必要且缺乏組織的 `using` 指示詞會使原始程式碼隨著時間而變得繁雜難以閱讀。 [組合管理 Using] 選項可移除未使用的 `using` 指示詞來精簡原始程式碼，並加以排序來改善可讀性。  
  
 若要查看 Visual Studio IDE 中的可用選項，請在 [編輯] 功能表上，指向 [IntelliSense]，然後指向 [組合管理 Using]。 IDE 提供下列選項來組合管理和移除 `usings` 指示詞：  
  
### <a name="implement-interface"></a>實作介面  
 在程式碼編輯器中工作時，IntelliSense 可提供協助您實作[介面](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba)的選項。 一般來說，若要正確地實作介面，必須為類別中介面的每位成員建立方法宣告。 使用 IntelliSense 會在您於類別宣告中輸入介面名稱後，顯示智慧標籤。 您可利用智慧標籤，選擇要使用明確或隱含命名的方式進行自動實作介面。 在明確命名的情況下，方法宣告會使用介面的名稱; 而在隱含命名的情況下，方法宣告則不會指出其所屬的介面。 明確命名的介面方法只可透過介面執行個體而不是透過類別執行個體加以存取。 如需詳細資訊，請參閱[明確介面實作](http://msdn.microsoft.com/library/181c901f-0d4c-4f29-97fc-895079617bf2)。  
  
 實作介面將會產生最少數目的滿足介面之方法虛設常式。 如果基礎類別實作部分的介面，則不會重新產生這些虛設常式。  
  
### <a name="implement-abstract-base-class"></a>實作抽象基底類別  
 在使用 [程式碼編輯器] 時，IntelliSense 提供您可自動實作抽象基底類別成員的選項。 一般而言，實作抽象基底類別的成員需要針對衍生類別中抽象基底類別的每個方法建立新的方法定義。 使用 IntelliSense，在類別宣告中輸入抽象基底類別的名稱後，就會顯示智慧標籤。 智慧標籤提供您自動實作基底類別方法的選項。  
  
 [實作抽象基底類別] 功能所產生的方法虛設常式是由定義在 MethodStub.snippet 檔案中的程式碼片段所模式化。 程式碼片段是可以修改的。 如需詳細資訊，請參閱[逐步解說：建立程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)。  
  
### <a name="generate-from-usage"></a>使用時產生  
 [使用時產生] 功能可讓您直接使用類別和成員，而不需要先行定義。 您可以為任何想要使用但尚未定義的類別、建構函式、方法、屬性、欄位或列舉，產生虛設常式。 您可以產生新類型和成員，不用離開目前在程式碼中的位置。 這可將對工作流程的干擾降至最低。  
  
 每個未定義的識別碼下都會顯示波浪底線。 當您將滑鼠指標放在識別碼時，工具提示中就會出現錯誤訊息。  
  
 若要顯示適當的選項，您可以使用下列其中一項程序：  
  
- 按一下未定義的識別碼。 最左邊的字元下會出現短底線。 將滑鼠指標停留在短底線，就會顯示智慧標籤 (圖示)。 按一下智慧標籤。  
  
- 按一下未定義的識別碼，然後再按 CTRL+. (句點)。  
  
- 以滑鼠右鍵按一下未定義的識別碼，然後按一下 [產生]。  
  
  顯示的選項包括：  
  
- **產生屬性虛設常式**  
  
- **產生欄位虛設常式**  
  
- **產生方法虛設常式**  
  
- **產生類別**  
  
- **產生新的類型** (針對類別、結構、介面或列舉)  
  
## <a name="generate-event-handlers"></a>產生事件處理常式  
 在程式碼編輯器中，IntelliSense 可協助您將方法 (事件處理常式) 連結到事件欄位。  
  
 當您在 .cs 檔案的事件欄位後輸入 `+=` 運算子時，IntelliSense 會提示您按下 TAB 鍵的選項。 這會插入委派的新執行個體，指向處理事件的方法。  
  
 ![按鈕自動連結](../ide/media/vxautohookup.gif "vxAutoHookUp")  
  
 如果按下 TAB，IntelliSense 會自動為您完成陳述式，並在程式碼編輯器中將事件處理常式參考顯示為選取的文字。 若要完成自動事件連結，IntelliSense 會提示您再次按下 TAB 鍵，為事件處理常式建立空白的虛設常式 。  
  
 ![產生事件處理常式](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")  
  
> [!NOTE]
> 如果 IntelliSense 建立的新委派，參考的是現有的事件處理常式，IntelliSense 就會在工具提示中傳達這項資訊。 接著您就可以修改此參考，程式碼編輯器中已選取該文字。 否則，自動事件連結即於此刻完成。  
  
 如果按下 TAB，IntelliSense 就會虛設出有正確簽章的方法，並將游標放在事件處理常式的主體中。  
  
> [!NOTE]
> 使用 [檢視] 功能表上的 [向後巡覽] 命令 (CTRL+-)，返回事件連結陳述式。  
  
 下列工作示範 IntelliSense 如何自動連結名為 `button1_Click` 的事件處理常式和名為 `button1.Click` 的事件欄位。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
