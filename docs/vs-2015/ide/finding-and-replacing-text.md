---
title: 尋找和取代文字 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 51d361bf74fb1181c64e5299b0925c262f185e9b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426326"
---
# <a name="finding-and-replacing-text"></a>Finding and Replacing Text
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 程式碼編輯器以及特定以文字為基礎的輸出視窗 (例如 [尋找結果] 視窗) 中，您可以使用 [尋找和取代] 控制項或 [檔案中尋找/取代] 來尋找和取代文字。 您也可以在某些設計工具視窗 (例如 XAML 設計工具和 Windows Forms 設計工具) 以及工具視窗中進行搜尋和取代。  
  
 您可以將搜尋範圍設為目前文件、目前方案或一組自訂的資料夾。 您也可以指定一組副檔名來搜尋多個檔案。 您可以使用 .NET 規則運算式來自訂搜尋語法。  
  
 若要尋找和取代規則運算式，請參閱[在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。  
  
> [!TIP]
> [尋找/命令] 方塊仍然是工具列控制項，但不再預設為可見。 您可以選擇 [標準] 工具列上的 [新增或移除按鈕]，然後選擇 [尋找]，以顯示 [尋找/命令] 方塊。 如需詳細資訊，請參閱[尋找/命令方塊](../ide/find-command-box.md)。  
  
## <a name="find-and-replace-control"></a>尋找和取代控制項  
 [尋找和取代] 控制項會出現在程式碼編輯器視窗的右上角。 [尋找和取代] 控制項會立即反白顯示目前文件中每個出現的指定搜尋字串。 您可以選擇搜尋控制項上的 [找下一個] 按鈕或 [找上一個] 按鈕，以從第一個出現位置巡覽至另一個出現位置。  
  
 您可以選擇 [尋找] 文字方塊旁的按鈕，以存取取代選項。 若要一次執行一個取代，請選擇 [取代] 文字方塊旁的 [取代下一個] 按鈕。 若要取代所有相符項目，請選擇 [全部取代] 按鈕。  
  
 若要變更相符項目的醒目提示色彩，請選擇 [工具] 功能表，並選取 [選項]，然後選擇 [環境]，再選取 [字型和色彩]。 在 [顯示設定] 清單中，選取 [文字編輯器]，然後在 [顯示項目] 清單中選取 [尋找醒目提示 (副檔名)]。  
  
### <a name="searching-tool-windows"></a>搜尋工具視窗  
 您可以選擇 [編輯] 功能表上的 [尋找和取代] 或 (CTRL+F)，以使用程式碼或文字視窗中的 [尋找] 控制項 (例如 [輸出] 視窗和 [尋找結果] 視窗)。  
  
 部分工具視窗中也提供 [尋找] 控制項的版本。 例如，您現在可以在搜尋方塊中輸入文字，以篩選 [工具箱] 視窗中的控制項清單。 現在可讓您搜尋其內容的其他工具視窗包含方案總管、[屬性] 視窗和 **Team Explorer** 等。  
  
## <a name="findreplace-in-files"></a>檔案中尋找/取代  
 [檔案中尋找/取代] 的運作方式與 [尋找和取代] 控制項類似，不同之處在於您可以定義搜尋範圍。 您不只可以在編輯器中搜尋目前開啟的檔案，還可以搜尋所有開啟的文件、整個方案、目前專案以及選取的資料夾集。 您也可以依副檔名進行搜尋。 若要存取 [檔案中尋找/取代] 對話方塊，請選擇 [編輯] 功能表 (或 CTRL+SHIFT+F) 上的 [尋找和取代]。  
  
 當您選擇 [全部尋找] 時，會開啟 [尋找結果] 視窗，並列出您搜尋的相符項目。 在清單中選取結果會顯示相關聯的檔案，並反白顯示相符項目。 如果尚未開啟檔案進行編輯，則會在索引標籤牆右側的預覽索引標籤中開啟它。 您可以使用 [尋找] 控制項來搜尋 [尋找結果] 清單。  
  
### <a name="creating-custom-search-folder-sets"></a>建立自訂搜尋資料夾集  
 您可以選擇 [查詢] 方塊旁的 [選擇搜尋資料夾] 按鈕 (看起來就像 **…**)，來定義搜尋範圍。 在 [選擇搜尋資料夾] 對話方塊中，您可以指定一組要在其中搜尋的資料夾，並且可以儲存規格，以在稍後重複使用。 只有在您已將遠端電腦的磁碟機對應到本機電腦時，才能在遠端電腦上指定資料夾。  
  
### <a name="creating-custom-component-sets"></a>建立自訂元件集  
 您可以選擇 [查詢] 方塊旁的 [編輯自訂元件集] 按鈕，將元件集定義為搜尋範圍。 您可以指定已安裝的 .NET 或 COM 元件、方案中所含的 Visual Studio 專案，或者任何組件或類型庫 (.dll、.tlb、.olb、.exe 或 .ocx)。 若要搜尋參考，請選取 [查詢參考] 方塊。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)
