---
title: 程式碼巡覽命令
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1263b7a0ae65731eb618ffc925ff0f6310be0f4d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919506"
---
# <a name="navigate-code"></a>巡覽程式碼

Visual Studio 提供許多方式在編輯器中巡覽程式碼。 本主題會摘要說明不同的程式碼巡覽方式，並提供詳細資訊的主題連結。

## <a name="navigate-backward-and-navigate-forward-commands"></a>向後巡覽和向前巡覽命令

您可以使用工具列上的 [向後巡覽]  \(**Ctrl**+ **-** )和 [向前巡覽]  \(**Ctrl**+**Shift**+ **-** )按鈕，將插入點移至上一個位置或回到離上一個位置最近的位置。 這些按鈕會保留插入點的最後 20 個位置。 [檢視]  功能表的 [向後巡覽]  和 [向前巡覽]  底下也有這些命令。

![[向前] 及 [向後] 導覽按鈕](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>巡覽列

您可以使用**巡覽列**，也就是程式碼視窗頂端的下拉式清單方塊，在程式碼基底中巡覽程式碼。 只要選擇類型或成員，就可以直接移至類型或成員。 編輯 Visual Basic、C# 或 C++ 程式碼基底中的程式碼時，會顯示巡覽列。 在部分類別中，可能會停用在目前程式碼檔案外部定義的成員 (以灰色顯示)。

![程式碼巡覽列](../ide/media/vside_navigation_bar.png)

您可以巡覽各下拉式方塊，如下所示：

- 若要巡覽至目前檔案所屬的另一個專案，請在左側下拉式清單中選擇它。

- 若要巡覽至類別或類型，請在中間的下拉式清單中選擇它。

- 若要直接巡覽至類別中的程序或其他成員，請在右側下拉式清單中選擇它。

- 若要將焦點從程式碼視窗移至導覽列，請按快速鍵組合 **Ctrl**+**F2**。

- 若要將焦點從巡覽列的某個方塊移至另一個方塊，請按 **Tab** 鍵。

- 若要選取具有焦點的巡覽列項目並返回程式碼視窗，請按 **Enter** 鍵。

- 若要將焦點從巡覽列回復到程式碼，但不選取任何項目，請按 **Esc** 鍵。

若要隱藏導覽列，請在 [文字編輯器所有語言]  設定 ([工具]   > [選項]   > [文字編輯器]   > [所有語言]  ) 中變更 [導覽列]  選項，或變更各個語言的設定。

## <a name="find-all-references"></a>尋找所有參考

在解決方案中尋找選取項目的所有參考。 您可以使用它來檢查大型重構可能的副作用，並驗證「無作用」程式碼。 按 **F8** 在結果之間移動。 如需詳細資訊，請參閱[在程式碼中尋找參考](finding-references.md)。

輸入 | 功能
------------ | ---
**鍵盤** | 將文字資料指標放在類型名稱內的某個位置，然後按 **Shift**+**F12**
**滑鼠** | 從右鍵功能表中選取 [尋找所有參考] 

## <a name="reference-highlighting"></a>反白顯示參考

當您按一下原始程式碼中的符號時，該符號在文件的所有出現處，都將反白顯示。 反白顯示的符號可能包含宣告和參考，以及許多其他 [尋找所有參考]  會傳回的符號。 其中包括類別、物件、變數、方法和屬性的名稱。 在 Visual Basic 程式碼中，許多控制項結構的關鍵字也會反白顯示。 若要移到下一個或上一個反白顯示的符號，請按 **Ctrl**+**Shift**+**向下鍵**或 **Ctrl**+**Shift**+**向上鍵**。 您可以變更 [工具]   > [選項]   > [環境]   > [字型和色彩]   > [反白顯示的參考]  中的反白顯示色彩。

## <a name="go-to-commands"></a>移至命令

移至有下列命令，位於 [編輯]  下的 [移至]  ：

- **移至指定行** (**Ctrl**+**G**)：移至作用中文件的指定行號。

- **移至全部** (**Ctrl**+**T** 或 **Ctrl**+ **,** )：移至指定的行、類型、檔案、成員或符號。

- **移至檔案** (**Ctrl**+**1**、**Ctrl**+**F**)：移至解決方案中的指定檔案。

- **移至最近使用的檔案** (**Ctrl**+**1**、**Ctrl**+**R**)：移至方案中指定的最近瀏覽檔案。

- **移至類型** (**Ctrl**+**1**、**Ctrl**+**T**)：移至解決方案中的指定類型。

- **移至成員** (**Ctrl**+**1**、**Ctrl**+**M**)：移至解決方案中的指定成員。

- **移至符號** (**Ctrl**+**1**、**Ctrl**+**S**)：移至解決方案中的指定符號。

在 Visual Studio 2017 15.8 及更新版本中，也可以使用下列**移至**巡覽命令：

- **移至檔案中的下一個問題** (**Alt**+**PgDn**) 及**移至檔案中的上一個問題** (**Alt**+**PgUp**)

- **移至上次編輯位置** (**Ctrl**+**Shift**+**Backspace**)

如需深入了解這些命令，請參閱[使用移至命令來尋找程式碼](../ide/go-to.md)主題。

## <a name="go-to-definition"></a>移至定義

[移至定義] 會帶您到所選項目的定義。 如需詳細資訊，請參閱[移至定義和查看定義](../ide/go-to-and-peek-definition.md)。

輸入 | 功能
------------ | ---
**鍵盤** | 將文字游標放在類型名稱內的某個位置，然後按 **F12**
**滑鼠** | 以滑鼠右鍵按一下類型名稱，然後選取 [移至定義]  或按 **Ctrl**，然後按一下類型名稱

## <a name="peek-definition"></a>查看定義

[查看定義] 會在視窗中顯示所選項目的定義，您不用離開目前所在程式碼編輯器的位置。 如需詳細資訊，請參閱[如何：使用查看定義來檢視及編輯程式碼](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)以及[移至定義和查看定義](../ide/go-to-and-peek-definition.md)。

輸入 | 功能
------------ | ---
**鍵盤** | 將文字資料指標放在類型名稱內的某個位置，然後按 **Alt**+**F12**
**滑鼠** | 以滑鼠右鍵按一下類型名稱，然後選取 [查看定義]  或按 **Ctrl**，再按一下類型名稱 (如已勾選 [在預覽檢視中開啟定義]  選項)

## <a name="go-to-implementation"></a>移至實作

使用 [前往實作] 從基底類別或類型巡覽至其實作。 如果有多個實作，您會看到它們列在 [尋找符號結果]  視窗中︰

輸入 | 功能
------------ | ---
**鍵盤** | 將文字資料指標放在類型名稱內的某個位置，然後按 **Ctrl**+**F12**
**滑鼠** | 以滑鼠右鍵按一下類型名稱，然後選取 [移至實作] 

## <a name="call-hierarchy"></a>呼叫階層

您可以在[呼叫階層視窗](../ide/reference/call-hierarchy.md)中檢視對方法的呼叫和來自方法的呼叫：

輸入 | 功能
------------ | ---
**鍵盤** | 將文字資料指標放在類型名稱內的某個位置，然後按 **Ctrl**+**K**、**Ctrl**+**T**
**滑鼠** | 以滑鼠右鍵按一下成員名稱，然後選取 [檢視呼叫階層] 

## <a name="next-method-and-previous-method-commands-visual-basic"></a>下一個方法和上一個方法命令 (Visual Basic)

在 Visual Basic 程式碼檔案中，使用這些命令可將插入點移動至不同的方法。 選擇 [編輯]   > [下一個方法]  或 [編輯]   > [上一個方法]  。

## <a name="structure-visualizer"></a>結構視覺化檢視

程式碼編輯器中的結構視覺化檢視功能會顯示「結構輔助線」  ，這是垂直虛線，用來指出程式碼基底中的成對大括弧。 這可讓您更輕鬆地查看邏輯區塊的開始和結束位置。

![結構視覺化檢視](../ide/media/vside_structure_visualizer.png)

若要停用結構輔助線，請移至 [工具]   > [選項]   > [文字編輯器]   > [一般]  ，並清除 [顯示結構輔助線]  方塊。

## <a name="enhanced-scroll-bar"></a>增強型捲軸

您可以使用程式碼視窗中的進階捲軸，以取得程式碼的鳥瞰檢視。 在地圖模式中，當您在捲軸上向上及向下移動游標時，可以預覽程式碼。 如需詳細資訊，請參閱[如何：透過自訂捲軸的方式追蹤程式碼](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)。

## <a name="codelens-information"></a>CodeLens 資訊

當您在程式碼編輯器中使用 CodeLens 時，可以尋找特定程式碼的相關資訊，例如變更及進行這些變更的人員、參考、Bug、工作項目、程式碼檢閱和單元測試狀態。 當您使用 Visual Studio Enterprise 與 Team Foundation Server 時，CodeLens 將以類似抬頭顯示方式執行。 請參閱[尋找程式碼變更和其他記錄](../ide/find-code-changes-and-other-history-with-codelens.md)。

## <a name="see-also"></a>另請參閱

- [程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)
- [檢視呼叫階層](../ide/reference/call-hierarchy.md)
