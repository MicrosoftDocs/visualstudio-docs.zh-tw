---
title: "在程式碼中尋找參考 | Microsoft Docs"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92c12e4d51255849843f938c032ca17b611eeeab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="finding-references-in-your-code"></a>在程式碼中尋找參考  
您可以使用 [尋找所有參考] 命令，來尋找在整個程式碼基底中參考特定程式碼項目的位置。 在您想要尋找其參考之項目的操作 (右鍵) 功能表上會提供 [尋找所有參考] 命令。 或者，如果您是鍵盤使用者，請按 **Shift + F12**。  

結果會顯示在名為 **'*element*' references** 的工具視窗中，其中*element* 是所搜尋項目的名稱。 [參考] 視窗中的工具列可讓您︰  
- 變更下拉式清單方塊中的搜尋範圍。 您可以選擇只查看整個方案中變更的文件。  
- 選擇 [複製] 按鈕，以複製所選取的參考項目。  
- 選擇按鈕以移至清單中的下一個或上一個位置，或按 **F8** 和 **Shift + F8** 鍵執行同樣的動作。  
- 選擇 [清除所有篩選條件] 按鈕，以移除所傳回結果上的任何篩選條件。  
- 選擇 [群組依據:] 下拉式清單方塊中的設定，以變更所傳回項目的群組依據。  
- 選擇 [保存結果] 按鈕，以保存目前搜尋結果視窗。 當您選擇此按鈕時，目前搜尋結果會停留在此視窗中，而新的搜尋結果會出現在新的工具視窗中。  
- 在 [搜尋 [尋找所有參考]] 文字方塊中輸入文字，以搜尋搜尋結果內的字串。  

您也可以將滑鼠指標停留在任何搜尋結果上方，以查看參考的預覽。  

![[尋找所有參考] 工具視窗](../ide/media/vside_findallreferences.png)  

### <a name="navigate-to-references"></a>巡覽至參考
您可以使用下列方法來巡覽至 [參考] 視窗中的參考：  

- 按 **F8** 鍵以移至下一個參考，或選擇 **Shift + F8** 鍵以移至上一個參考。  
- 在參考上按 **Enter** 鍵，或按兩下參考，以移至它在程式碼中的位置。  
- 在參考的操作功能表上，選擇 [移至上一個位置] 或 [移至下一個位置] 命令。  
- 選擇 [向上鍵] 和 [向下鍵] (如果已在 [選項] 對話方塊中啟用)。 若要啟用此功能，請在功能表列上選擇 [工具]、[選項]、[環境]、[索引標籤和視窗]、[預覽索引標籤]，然後選取 [允許在預覽索引標籤中開啟新檔案] 和 [在 [尋找結果] 中預覽選取的檔案] 方塊。  

### <a name="change-reference-groupings"></a>變更參考群組  
預設會先依專案來分組參考，然後依定義進行分組。 不過，您可以變更工具列之 [群組依據:] 下拉式清單方塊中的設定，來變更此群組順序。 例如，您可以將它從 [專案接著定義] 的預設設定變更為 [定義接著專案]，以及其他設定。  

[定義] 和 [專案] 使用兩個預設群組，但您可以選擇所選取項目之操作功能表上的 [群組] 命令來新增其他群組。 如果您的方案有大量檔案和路徑，則新增更多群組十分有用。  

## <a name="see-also"></a>另請參閱  
[巡覽程式碼](../ide/navigating-code.md)  