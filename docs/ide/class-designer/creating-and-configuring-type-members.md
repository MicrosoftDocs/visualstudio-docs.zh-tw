---
title: 建立和設定類型成員 (類別設計工具)
description: 瞭解如何將成員新增至類別圖表上的類型，以及在 [類別細節] 視窗中設定這些成員。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 897001a5ac10e8a8e1eef96feca4113afa5e1ebf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880563"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>在類別設計工具中建立及設定類型成員

您可以將這些成員新增至某個類別圖表上的類型，以及在 [類別細節] 視窗中設定這些成員：

|**型別**|**可以包含的成員**|
|--------------| - |
|類別|方法、屬性 (針對 C# 和 Visual Basic)、欄位、事件 (針對 C# 和 Visual Basic)、建構函式 (方法)、解構函式 (方法)、常數|
|列舉|member|
|介面|方法、屬性、事件 (針對 C# 和 Visual Basic)|
|抽象類別|方法、屬性 (針對 C# 和 Visual Basic)、欄位、事件 (針對 C# 和 Visual Basic)、建構函式 (方法)、解構函式 (方法)、常數|
|結構 (Structure) (C# 中的結構 (Struct))|方法、屬性 (針對 C# 和 Visual Basic)、欄位、事件 (針對 C# 和 Visual Basic)、建構函式 (方法)、常數|
|代理人|參數|
|模組 (僅限 VB)|方法、屬性、欄位、事件、建構函式、常數|

> [!NOTE]
> 使用自動實作屬性 (僅限 C#) 可在屬性的 get 與 set 存取子不需要額外邏輯時，讓屬性宣告更為簡明。 若要顯示完整簽章，請從 [類別圖表] 功能表中選擇 [變更成員格式] > [顯示完整簽章]。 如需自動實作屬性的詳細資訊，請參閱[自動實作的屬性](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)。

## <a name="common-tasks"></a>常見工作

|Task|支援內容|
|----------| - |
|**開始使用：** 您必須先開啟 [類別細節] 視窗，才可建立及設定類型成員。|- [開啟 [類別細節] 視窗](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [類別細節使用注意事項](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [顯示唯讀資訊](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [類別圖表和類別細節視窗中的鍵盤和滑鼠快捷方式](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**建立和修改類型成員：** 您可以使用 [類別細節] 視窗來建立新的成員、修改成員，以及將參數新增至方法。|- [建立成員](creating-and-configuring-type-members.md#create-members)<br />- [修改類型成員](creating-and-configuring-type-members.md#modify-type-members)<br />- [將參數加入至方法](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>開啟類別細節視窗

依預設，當您開啟新的類別圖表時會自動出現 [類別細節] 視窗。 請參閱 [如何：將類別圖表加入至專案](how-to-add-class-diagrams-to-projects.md)) 。 您也可以採用下列方式開啟 [類別細節]視窗：

- 在圖表中的任一類別上按一下滑鼠右鍵以顯示操作功能表，然後選取 [類別細節]。

-   >  從功能表列中選取 [查看 **其他 Windows**  >  **類別的詳細資料**]。

## <a name="create-members"></a>建立成員

您可以使用下列任何工具建立成員：

- **類別設計工具**

- [類別細節] 視窗工具列

- [類別細節] 視窗

> [!NOTE]
> 您也可以使用本章節中的程序建立建構函式和解構函式。 請記住，建構函式和解構函式是特殊類型的方法，因此它們會出現在類別圖表圖形的 [方法] 區間以及 [類別細節] 視窗方格的 [方法] 區段中。

> [!NOTE]
> 參數是您唯一可以加入委派的實體。 請注意，標題為「使用 [類別細節] 視窗工具列建立成員」的程序對此動作無效。

### <a name="create-a-member-using-class-designer"></a>使用類別設計工具建立成員

1. 以滑鼠右鍵按一下您要新增成員的類型，並指向 [新增]，然後選擇您要新增的成員類型。

     如此就會建立新成員簽章並加入至類型。 新成員簽章會有預設名稱，稍後您可以在 [類別設計工具]、[類別細節] 視窗或 [屬性] 視窗中進行變更。

2. 您可以選擇性地指定類型等其他成員相關資訊。

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>使用 [類別細節] 視窗工具列建立成員

1. 在圖表介面上選取您要加入成員的類型。

     類型會取得焦點，而其內容會顯示於 [類別細節] 視窗。

2. 在 [**類別細節**] 視窗工具列中，按一下上方圖示，然後從下拉式清單中選取 [**新增 \<member>** ]。

     游標會針對要新增的成員類型移至列的 [名稱] 欄位。 例如，如果按一下 [新增屬性]，資料指標會移至 [類別細節] 視窗上 [屬性] 區段中的新一列。

3. 輸入您要建立的成員名稱，並且按 Enter 鍵 (或是做些按 Tab 鍵之類的動作移開焦點)。

     如此就會建立新成員簽章並加入至類型。 現在成員就會存在於程式碼中，並顯示於 [類別設計工具]、[類別細節] 視窗和 [屬性] 視窗。

4. 您可以選擇性地指定類型等其他成員相關資訊。

### <a name="create-a-member-using-the-class-details-window"></a>使用 [類別細節] 視窗建立成員

1. 在圖表介面上選取您要加入成員的類型。

     類型會取得焦點，而其內容會顯示於 [類別細節] 視窗。

2. 在 [ **類別細節** ] 視窗中，于包含您要新增之成員類型的區段中，按一下 **\<add member>** 。 例如，如果您想要新增欄位，請按一下 **\<add field>** 。

3. 輸入您要建立的成員名稱，並且按 Enter 鍵。

     如此就會建立新成員簽章並加入至類型。 現在成員就會存在於程式碼中，並顯示於 [類別設計工具]、[類別細節] 視窗和 [屬性] 視窗。

4. 您可以選擇性地指定類型等其他成員相關資訊。

    > [!NOTE]
    > 您也可以使用鍵盤快速鍵來建立成員。 如需詳細資料，請參閱[類別圖表和類別細節視窗中的鍵盤和滑鼠快速鍵](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)。

## <a name="modify-type-members"></a>列舉類型成員

[類別設計工具] 可讓您修改圖表中所顯示類型的成員。 只要在類別圖中顯示的類型並非唯讀，您都可以修改其成員。 您可以在設計介面、[屬性] 視窗和 [類別細節] 視窗上使用就地編輯，以修改類型成員。

所有在 [類別細節] 視窗中顯示的成員，都代表在類別圖表中的類型成員。 成員分成四種類型：方法、屬性、欄位和事件。

所有成員列都會出現在依照類型群組成員的標題底下。 例如，所有屬性都會出現在 [屬性] 標題底下；標題是方格中可以展開或摺疊的節點。

每個成員列都會顯示下列項目：

- **成員圖示**

     各成員類型都會顯現自己的圖示。 將滑鼠指向成員圖示以顯示成員簽章。 按一下成員圖示或成員圖示左邊的空白處，以選取那一列。

- **成員名稱**

     成員列中的 [名稱] 欄會顯示成員的名稱。 這個名稱也會顯示於 [屬性] 視窗的 [名稱] 屬性中。 您可以使用這個儲存格，變更任何具有讀寫權限的成員名稱。

     如果 [名稱] 欄太窄而無法顯示完整名稱，將滑鼠指向成員名稱就會顯示完整名稱。

- **成員類型**

     **MemberType** 儲存格使用 IntelliSense，讓您能從目前專案或參考專案中所有可用類型的清單中選取。

- **成員修飾詞**

     將成員的可視性修飾詞變更為 `Public` (`public`)、`Private` (`private`)、`Friend` (`internal`) `Protected` (`protected`)、`Protected Friend` (`protected internal`) 或 `Default`。

- **\<add member>**

     [ **類別細節** ] 視窗中的最後一個資料列包含 [ **\<add member>** **名稱** ] 儲存格中的文字。 如果按一下這個儲存格，便會建立新的成員。 如需詳細資訊，請參閱[建立成員](creating-and-configuring-type-members.md#create-members)。

- **屬性視窗中的成員屬性**

     [類別細節] 視窗會顯示 [屬性] 視窗中出現的成員屬性的子集。 在一個位置變更屬性，便會在全域變更該屬性的值。 這包括在其他位置顯示的屬性值。

- **總結**

     [摘要] 儲存格會公開成員的相關資訊摘要。 按一下 [摘要] 儲存格中的省略符號，即可檢視或編輯成員之 [摘要]、[傳回型別] 和 [備註] 的相關資訊。

- [隱藏] 

     如果選取 [隱藏] 核取方塊，類型中將不會顯示成員。

### <a name="to-modify-a-type-member"></a>若要修改類型成員

1. 使用 [類別設計工具] 選取類型。

2. 如果未顯示 [類別細節] 視窗，請按一下 [類別設計工具] 工具列上的 [類別細節] 視窗按鈕。

3. 編輯 [類別細節] 視窗方格欄位中的值。 每次編輯之後都要按 ENTER，或讓焦點離開已編輯的欄位 (例如按下 TAB)。 您所進行的編輯會立即反應在程式碼中。

    > [!NOTE]
    > 如果您只想要修改成員的名稱，可以透過就地編輯來進行。

## <a name="add-parameters-to-methods"></a>將參數新增至方法

您可以使用 [類別細節] 視窗將參數新增至方法。 參數可以設定為必要或是選擇性。 如果提供參數的 [選擇性預設值] 屬性值，即可指示設計工具產生程式碼作為選擇性參數。

參數列包含下列項目：

- **名稱**

     參數列的 [名稱] 欄會顯示參數的名稱。 這個名稱也會顯示於 [屬性] 視窗的 [名稱] 屬性中。 如果您具備任何參數的讀寫權限，可以使用這個儲存格來變更參數名稱。

     如果 [名稱] 欄太窄而無法顯示完整名稱，將滑鼠指向參數名稱就會顯示參數的名稱。

- **型別**

     [ **參數類型** ] 儲存格使用 IntelliSense，可讓您從目前專案或參考專案中所有可用類型的清單中選擇。

- **修飾詞**

     參數列中的 [修飾詞] 儲存格可以接受並顯示參數的新修飾詞。 若要輸入新的參數修飾詞，請使用下拉式清單方塊，若在 C# 中請選取 [None]、[ref]、[out] 或 [params]，若在 VB 中則請選取 [ByVal]、[ByRef] 或 [ParamArray]。

- **總結**

     參數列中的 [摘要] 儲存格可讓您輸入程式碼註解，在程式碼編輯器中輸入參數時，該程式碼註解就會出現在 IntelliSense 中。

- **\<add parameter>**

     成員的最後一個參數列在 [名稱] 儲存格中包含 **<新增參數\>** 字樣。 按一下這個儲存格即可建立新參數。 如需詳細資訊，請參閱[將參數新增至方法](creating-and-configuring-type-members.md#add-parameters-to-methods)。

[ **屬性** ] 視窗會顯示 [ **類別細節** ] 視窗中顯示的相同參數屬性： **名稱**、 **類型**、 **修飾** 詞、 **摘要**，以及 **選用的預設** 屬性。 在其中一個位置變更屬性將會全域更新屬性值，包括在另一個位置的顯示值。

> [!NOTE]
> 若要將參數新增至委派，請參閱[建立成員](creating-and-configuring-type-members.md#create-members)。

> [!NOTE]
> 雖然解構函式是方法，但是卻不能擁有參數。

### <a name="to-add-a-parameter-to-a-method"></a>若要將參數加入至方法

1. 在圖表介面上按一下類型 (其中內含要加入參數的方法)。

     類型會取得焦點，而其內容會顯示於 [類別細節] 視窗。

2. 在 [類別細節] 視窗上，展開要新增參數的方法所屬列。

     縮排的參數資料列隨即出現，其中只包含一對括弧和單字 **\<add parameter> 。**

3. 按一下 **\<add parameter>** ，輸入新參數的名稱，然後按 **enter**。

     如此，便會將新參數新增至方法以及方法的程式碼中。 [類別細節] 和 [屬性] 視窗中便會顯示新的參數。

4. 您可以選擇性地指定類型等其他參數相關資訊。

### <a name="to-add-an-optional-parameter-to-a-method"></a>若要將選擇性參數加入至方法

1. 在圖表介面上按一下類型 (其中內含要加入選擇性參數的方法)。

     類型會取得焦點，而其內容會顯示於 [類別細節] 視窗。

2. 在 [類別細節] 視窗上，展開要新增選擇性參數的方法所屬列。

     縮排的參數資料列隨即出現，其中只包含一對括弧和單字 **\<add parameter> 。**

3. 按一下 **\<add parameter>** ，輸入新參數的名稱，然後按 **enter**。

     如此，便會將新參數新增至方法以及方法的程式碼中。 [類別細節] 和 [屬性] 視窗中便會顯示新的參數。

4. 在 [屬性] 視窗中，鍵入 [選擇性預設值] 屬性的值。 設定參數的 [選擇性預設值] 屬性會讓該參數成為選擇性。

    > [!NOTE]
    > 選擇性參數必須是參數清單中的最後一個參數。

## <a name="class-details-usage-notes"></a>[類別細節] 使用注意事項

請注意下列有關使用 [類別細節] 視窗的祕訣。

### <a name="editable-and-non-editable-cells"></a>可編輯和不可編輯的儲存格

[類別細節] 視窗中的儲存格幾乎全部都可以編輯，只有少數例外：

- 例如，當類型位於參考組件時，整個類型會處於唯讀狀態。 當您在 [類別設計工具] 中選擇圖形時，[類別細節] 視窗會以唯讀狀態顯示圖形的詳細資料。

- 索引子 (Indexer) 的名稱會是唯讀的，而其他項目 (類型、修飾詞 (Modifier)、摘要) 都可以編輯。

- 所有的泛型 (Generic) 在 [類別細節] 視窗中都具備唯讀參數。 若要變更泛型參數，請編輯其原始程式碼。

- 凡是類型參數名稱定義於泛型類型，該類型參數名稱就會是唯讀。

- 當類型的程式碼已損毀 (無法剖析)，[類別細節] 視窗會將類型內容以唯讀狀態顯示。

### <a name="the-class-details-window-and-source-code"></a>[類別細節] 視窗和原始程式碼

- 您可以在 [類別細節] 視窗 (或 [類別設計工具]) 中的圖形上按一下滑鼠右鍵，再按一下 [檢視程式碼]，即可檢視原始程式碼。 原始程式碼檔會開啟並捲動至選取的項目。

- 原始程式碼一變更，立即就會反應在 [類別設計工具] 和 [類別細節] 視窗顯示的簽章資訊上。 如果當時已經關閉 [類別細節] 視窗，則下次開啟視窗時就會看到新的資訊。

- 當類型的程式碼已損毀 (無法剖析)，[類別細節] 視窗會將類型內容以唯讀狀態顯示。

### <a name="clipboard-functionality-in-the-class-details-window"></a>[類別細節] 視窗中的剪貼簿功能

您可以從 [類別細節] 視窗複製或剪下欄位或列，然後貼到其他類型。 只有列不是處於唯讀狀態時，您才能夠剪下。 當您貼上列時，[類別細節] 視窗會指派新名稱 (由已複製的列衍生而來) 以避免發生衝突。

## <a name="display-of-read-only-information"></a>顯示唯讀資訊

[類別設計工具] 和 [類別細節] 視窗可以顯示下列項目的類型 (以及類型成員)：

- 包含類別圖的專案

- 包含類別圖的專案所參考的專案

- 包含類別圖的專案所參考的組件

在後面兩種情況下，參考的實體 (類型或成員) 在表示的類別圖中為唯讀。

整個專案或部分專案 (例如個別檔案) 可能為唯讀。 下列是專案或專案中某個檔案為唯讀的最常見情況：當專案在原始程式碼控制之下 (而且未被簽出)、存在外部組件中，或是作業系統將檔案視為唯讀。

**原始程式碼控制**

由於類別圖表是儲存為專案中的檔案，所以您要簽出專案以儲存在 [類別設計工具] 或 [類別細節] 視窗中所做的變更。

**唯讀專案**

專案可能會由於原始程式碼控制以外的原因而成為唯讀。 關閉專案時會顯示對話方塊詢問要覆寫專案檔、捨棄變更 (不儲存) 或取消關閉作業。 如果您選擇覆寫，專案檔就會被覆寫並成為可讀寫。 而且會加入新的類別圖檔。

**唯讀類型**

如果您嘗試儲存的專案其內含類型的原始程式碼檔為唯讀，就會出現 [儲存唯讀檔案] 對話方塊，讓您選擇要以新名稱或新位置儲存檔案，還是要覆寫唯讀檔案。 如果選擇覆寫檔案，新的複本就不再是唯讀檔案。

如果程式碼檔內含語法錯誤，檔案中顯示程式碼的圖案會暫時成為唯讀，直到修正語法錯誤為止。 處於此狀態的圖案會顯示紅色字體及紅色圖示，顯示「原始程式碼檔內含剖析錯誤」工具提示。

在類別設計工具的設計介面上會將存在於另一個專案節點或參考組件節點之下的參考型別 (例如 .NET 型別) 指示為唯讀。 存在於已開啟專案中的類型 (由該專案所定義) 為可讀寫，而其位於類別設計工具設計介面上的圖案也是指示為可讀寫。

程式碼和 [類別細節] 視窗中的索引子為可讀寫，但是索引子的名稱為唯讀。

您無法使用 [類別設計工具] 或 [類別細節] 視窗編輯部分方法；必須使用程式碼編輯器進行編輯。

您無法使用 [類別設計工具] 或 [類別細節] 視窗編輯原生 C++ 程式碼；必須使用程式碼編輯器編輯原生 C++ 程式碼。

## <a name="see-also"></a>另請參閱

- [檢視類型與關聯性](designing-and-viewing-classes-and-types.md)
- [重構類別和類型](refactoring-classes-and-types.md)
