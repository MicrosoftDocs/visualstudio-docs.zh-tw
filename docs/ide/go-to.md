---
title: "移至 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3b812629bf0f655f39c35a56eb1b3ca9113303a6
ms.openlocfilehash: 8bf6d49b21d128d15f5312fb230d4a8e7a8195af
ms.contentlocale: zh-tw
ms.lasthandoff: 03/01/2017

---

# <a name="go-to"></a>到
有許多方法可以透過鍵盤和滑鼠在 Visual Studio IDE 內輕鬆地巡覽程式碼。

<!-- VERSIONLESS -->
## <a name="go-to-all"></a>移至全部
Visual Studio 2017 及更新版本有提供這項功能，  其可巡覽程式碼，以找到您所尋找的特定位元。  您可以透過簡潔的整合介面，搜尋特定行、類型、符號、檔案和其他項目。

### <a name="how-to-use"></a>如何使用
* **鍵盤**
  * 按 **Ctrl+** 或 **Ctrl+T**  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
* **滑鼠**
  * 選取 [編輯] > [移至] > [移至全部]。

這預設會在 IDE 的右上方顯示一個小型視窗。

![移至全部](media/gotoall.png)

在這裡，有幾種方式可以繼續：
* 使用文字方塊下方選取的[篩選圖示](#filtered-searches)，輸入要搜尋且沒有前置詞的文字。
* 輸入後接要搜尋之文字的[前置詞](#filtered-searches)。
* 輸入問號 (?) 以取得其他說明。
  ![移至全部說明](media/gotoall_help.png)

### <a name="filtered-searches"></a>篩選的搜尋
若要將搜尋範圍縮小為特定類型，您可以在輸入時使用前置詞，或使用搜尋視窗下方的圖示，如下所示。

前置詞 | 圖示 | 快速鍵 | 說明
:----: | ---- | -------- | ---
#      | ![符號圖示](media/gotoall_symbolicon.png) | Ctrl+1、Ctrl+S | 尋找相符的符號
f      | ![檔案圖示](media/gotoall_fileicon.png)     | Ctrl+1、Ctrl+F | 尋找相符的檔名
m      | ![成員圖示](media/gotoall_membericon.png) | Ctrl+1、Ctrl+M | 尋找相符的成員
t      | ![類型圖示](media/gotoall_typeicon.png)     | Ctrl+1、Ctrl+T | 尋找相符的類型
:      | ![行圖示](media/gotoall_lineicon.png)     | Ctrl+G         | 移至輸入的行號

### <a name="search-locations"></a>搜尋位置
若要將搜尋範圍縮小為特定位置，請使用兩個文件圖示。

圖示 | 說明
---- | ---
![目前文件](media/gotoall_currentdocument.png) | 僅搜尋目前文件
![外部文件](media/gotoall_external.png) | 除了專案/方案中的文件之外，還會搜尋外部文件

### <a name="settings"></a>設定
按一下齒輪圖示 ![齒輪圖示](media/gotoall_gear.png) (位於右下方) 可讓您變更這項功能的運作方式。

設定 | 說明
------- | ---
使用預覽索引標籤 | 在 IDE 的預覽索引標籤中立即顯示選取的項目
顯示詳細資料    | 在視窗中顯示文件註解中的專案、檔案、行和摘要資訊
置中視窗   | 將此視窗移至 IDE 的中心，而不是右上方
<!-- END VERSIONLESS -->

## <a name="go-to-definition"></a>移至定義
巡覽至類型來源，然後在新的索引標籤中開啟結果︰

輸入        | 函式 
------------ | ---
**鍵盤** | 將文字游標放在類型名稱內的某個位置，然後按 **F12**
**滑鼠**    | 以滑鼠右鍵按一下類型名稱，然後選取 [移至定義]

## <a name="peek-definition"></a>查看定義
在快顯視窗中預覽類型的定義，而不是在新的索引標籤中︰

輸入        | 函式 
------------ | ---
**鍵盤** | 將文字游標放在類型名稱內的某個位置，然後按 **Alt+F12**
**滑鼠**    | 以滑鼠右鍵按一下類型名稱，然後選取 [查看定義]

如果您從快顯視窗查看另一個定義，則將開始階層連結路徑，而階層連結路徑可使用出現在快顯視窗上方的圓形和箭號進行巡覽。  如需詳細資訊，請參閱[如何：使用查看定義檢視和編輯程式碼 (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)。

## <a name="go-to-implementation"></a>移至實作
從基底類別或類型巡覽至其實作。  如果有多個實作，您會看到它們列在 [尋找符號結果] 視窗中︰

輸入        | 函式 
------------ | ---
**鍵盤** | 將文字游標放在類型名稱內的某個位置，然後按 **Ctrl+F12**
**滑鼠**    | 以滑鼠右鍵按一下類型名稱，然後選取 [移至實作]

## <a name="find-all-references"></a>尋找所有參考
尋找所有正在使用方法/屬性/變數的位置。  您可以使用此項目來驗證無作用程式碼，並檢查大型重構的可能副作用。  按 **F8** 在結果之間移動。

輸入        | 函式 
------------ | ---
**鍵盤** | 將文字游標放在類型名稱內的某個位置，然後按 **Ctrl+K、R**
**滑鼠**    | 以滑鼠右鍵按一下類型名稱，然後選取 [尋找所有參考]

## <a name="navigating-results"></a>巡覽結果
使用 Visual Studio 的巡覽功能時，可以前後巡覽堆疊︰

輸入        | 函式 
------------ | ---
**Ctrl+-**          | 向後巡覽堆疊
**Ctrl+Shift+-**    | 向前巡覽堆疊

您也可以使用 [檢視] > [向後巡覽] 和 [檢視] > [向前巡覽] 功能表項目。
