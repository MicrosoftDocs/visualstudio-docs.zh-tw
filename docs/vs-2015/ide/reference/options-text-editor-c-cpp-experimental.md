---
title: 選項、文字編輯器、C/C++、實驗 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 41be21f3b28cccfe735a2a908851ebe3b181ce7b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762891"
---
# <a name="options-text-editor-cc-experimental"></a>選項、文字編輯器、C/C++、實驗
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
藉由變更這些選項，您可以變更進行 C 或 C++ 程式設計時之 IntelliSense 和瀏覽資料庫的相關行為。  
  
 若要存取這個頁面，請在 [選項]  對話方塊的左窗格中依序展開 [文字編輯器] 和 [C/C++] ，然後選擇 [實驗] 。  
  
 Visual Studio 2015 Update 1 RC 安裝提供這些功能。  
  
> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## <a name="browsingnavigation"></a>瀏覽/巡覽  
 **啟用新的 Database Engine**  
 這應該會自動加速資料庫母體擴展，並讓 [移至定義]  和 [尋找所有參考] 等所有資料庫作業的速度變快 (而不會因此而失準) (只要關閉並重新開啟您的方案，即可套用變更，而不必重新啟動 Visual Studio)。  
  
## <a name="intellisense"></a>IntelliSense  
 **成員清單的點取代成箭號**  
 當成員清單適用時，以 '->' 取代 '.'。  
  
## <a name="refactoring"></a>重構  
 **啟用擷取函式**  
 將選取的程式碼擷取至其自己的函式，並以新函式的呼叫取代程式碼。 若要存取這項功能，請以滑鼠右鍵按一下選取的程式碼並選取 [快速動作] ，或是直接按預設快速鍵 Ctrl+點 [Ctrl+.]。  
  
 **啟用變更簽章**  
 加入、重新排列及刪除函式的參數，並將變更散佈到所有呼叫位置。 若要存取這項功能，請以滑鼠右鍵按一下函式並選取 [快速動作] ，或是直接按預設快速鍵 Ctrl+點 [Ctrl+.]。  
  
## <a name="text-editor"></a>文字編輯器  
 **啟用展開範圍**  
 如果啟用，您可以在文字編輯器中輸入 '{'，以大括號來括住選取的文字。  
  
 **啟用展開優先順序**  
 如果啟用，您可以在文字編輯器中輸入 '('，以圓括號來括住選取的文字。  
  
 如需 Visual Studio 組件庫中的其他文字編輯器功能，請參閱 [這裡](http://go.microsoft.com/fwlink/?LinkId=692016)的清單。 [C++ 快速修正](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)即為一例，其支援下列項目：  
  
- **加入遺漏的 #include** - 建議相關的 #include 來表示程式碼中的未知符號  
  
- **加入 Using 命名空間/完整限定符號** - 類似上一個項目，但針對命名空間  
  
- **加入遺漏的分號**  
  
- **MSDN 說明** - 搜尋 MSDN 中的錯誤訊息  
  
  您可以將游標停留在波浪線上，或是使用預設鍵盤快速鍵 Ctrl+點 (Ctrl +)，來取得燈泡。 請注意，針對鍵盤快速鍵，您的插入號不需要放在特定錯誤或語彙基元上；您可以直接在錯誤所在的同一行，叫用該行上任何項目的建議。  
  
## <a name="see-also"></a>請參閱  
 [設定語言特定編輯器選項](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refactoring in C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx) (在 C++ 中重構 (VC 部落格))
