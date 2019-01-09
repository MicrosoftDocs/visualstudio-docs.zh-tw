---
title: HOW TO：限制檢測特定函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e145a50c3fdb643affb67989ae11346bf7e30f9
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592855"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>HOW TO：限制檢測特定函式
您可以透過在 [效能工作階段] 或目標二進位檔屬性頁的 [進階] 頁面中設定選項，將檢測和資料收集限制在一或多個函式：  
  
- 如果您在效能工作階段屬性頁上指定函式，則在該工作階段所有已檢測的二進位檔上，都只會檢測這些函式。  
  
- 如果您在目標二進位檔的屬性頁上指定函式，就只會檢測在該特定二進位檔中的這些函式。 其他效能二進位檔中的函式仍會依照往例進行檢測。  
  
  只有在選取了檢測程式碼剖析方法時，才能支援這種限制資料收集的方式。  
  
> [!NOTE]
>  您也可以使用 [效能工作階段] 屬性頁的 [進階] 頁面，設定程式碼剖析工具 [VSInstr](../profiling/vsinstr.md) 命令列檢測工具可以使用的其他選項。  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>限制檢測效能工作階段中的特定函式  
  
1. 在 [效能總管] 中，以滑鼠右鍵按一下工作階段名稱，然後按一下 [屬性]。  
  
    [屬性頁] 對話方塊隨即出現。  
  
2. 在 [屬性頁] 對話方塊中，按一下 [進階]。  
  
3. 在 [其他檢測選項] 文字方塊中，使用下列語法輸入您要檢測之函式的名稱：  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` 是命名空間和函式名稱。 其格式為 `Namespace`**::**`FunctionName`。 請使用分號來分隔多個函式。 使用星號 (\*) 指定代表一或多個字元的萬用字元。 例如，**/include:MyNS::\\*** 可指定 MyNS 命名空間中的所有函式。  
  
   > [!NOTE]
   >  若要列出二進位檔中的函式，請在分析工具安裝目錄中開啟命令提示字元視窗 (請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md))，然後鍵入 **vsinstr /DumpFuncs**  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>限制檢測二進位檔中的特定函式  
  
1. 在 [效能總管] 中，從效能工作階段的 [目標] 節點中找出二進位檔名稱。  
  
2. 以滑鼠右鍵按一下二進位檔名稱，然後按一下 [屬性]。  
  
    [屬性頁] 對話方塊隨即顯示。  
  
3. 在 [屬性頁] 對話方塊中，按一下 [進階]。  
  
4. 在 [其他檢測選項] 文字方塊中，使用下列語法輸入您要檢測之函式的名稱：  
  
    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` 是命名空間和函式名稱。 其格式為 `Namespace`**::**`FunctionName`。 請使用分號來分隔多個函式。 使用星號 (\*) 指定代表一或多個字元的萬用字元。 例如，**/include:MyNS::\\*** 可指定 MyNS 命名空間中的所有函式。  
  
   > [!NOTE]
   >  若要列出二進位檔中的函式，請在分析工具安裝目錄中開啟命令提示字元視窗 (請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md))，然後鍵入 **vsinstr /DumpFuncs**  
  
## <a name="see-also"></a>另請參閱  
 [控制資料收集](../profiling/controlling-data-collection.md)   
 [如何：限制檢測特定 DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [如何：指定其他的檢測選項](../profiling/how-to-specify-additional-instrumentation-options.md)