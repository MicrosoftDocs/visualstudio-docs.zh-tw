---
title: 選項、文字編輯器、C-C++、實驗 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e4f239c5be290f6d79f52f55dbcb6da60d10785
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851693"
---
# <a name="options-text-editor-cc-experimental"></a>選項、文字編輯器、C/C++、實驗
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

藉由變更這些選項，您可以變更進行 C 或 C++ 程式設計時之 IntelliSense 和瀏覽資料庫的相關行為。

 若要存取這個頁面，請在 [選項] 對話方塊的左窗格中依序展開 [文字編輯器]和 [C/C++]，然後選擇 [實驗]。

 Visual Studio 2015 Update 1 RC 安裝提供這些功能。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 請參閱 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

## <a name="browsingnavigation"></a>瀏覽/巡覽
 **啟用新的資料庫引擎**這應該會自動加速資料庫擴展，並讓 [**移至定義**] 和 [**尋找所有參考**] 等作業的所有資料庫作業更快速（不會遺失精確度）。 (只要關閉並重新開啟您的方案，即可套用變更，而不必重新啟動 Visual Studio)。

## <a name="intellisense"></a>IntelliSense
 **成員清單-箭號**適用于成員清單時，以 '-> ' 取代 '. '。

## <a name="refactoring"></a>Refactoring
 **啟用解壓縮函數**將選取的程式碼解壓縮至它自己的函式，並使用新函式的呼叫來取代程式碼。 若要存取這項功能，請以滑鼠右鍵按一下選取的程式碼並選取 [快速動作]，或是直接按預設快速鍵 Ctrl+點 [Ctrl+.]。

 **啟用變更**簽章新增、重新排列和刪除函式的參數，並將變更傳播至所有呼叫位置。 若要存取這項功能，請以滑鼠右鍵按一下函式並選取 [快速動作]，或是直接按預設快速鍵 Ctrl+點 [Ctrl+.]。

## <a name="text-editor"></a>文字編輯器
 **啟用展開範圍**啟用時，您可以在文字編輯器中輸入 ' {'，以大括弧括住選取的文字。

 **啟用展開優先順序**啟用時，您可以在文字編輯器中輸入 ' （'，將選取的文字加上括弧以括住。

 如需 Visual Studio 組件庫中的其他文字編輯器功能，請參閱 [這裡](https://marketplace.visualstudio.com/)的清單。 [C++ 快速修正](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)即為一例，其支援下列項目：

- **加入遺漏的 #include** - 建議相關的 #include 來表示程式碼中的未知符號

- **加入 Using 命名空間/完整限定符號** - 類似上一個項目，但針對命名空間

- **加入遺漏的分號**

- **MSDN 說明** - 搜尋 MSDN 中的錯誤訊息

  您可以將游標停留在波浪線上，或是使用預設鍵盤快速鍵 Ctrl+點 (Ctrl +)，來取得燈泡。 請注意，針對鍵盤快速鍵，您的插入號不需要放在特定錯誤或語彙基元上；您可以直接在錯誤所在的同一行，叫用該行上任何項目的建議。

## <a name="see-also"></a>請參閱
 [在中C++ ](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/) [設定語言特定編輯器選項](../../ide/reference/setting-language-specific-editor-options.md)重構（VC Blog）
