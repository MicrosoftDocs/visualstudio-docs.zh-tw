---
title: HOW TO：限制檢測特定 DLL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b39689219b113343162aa0e814cfa68e2422f08d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597565"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>作法：限制檢測特定 DLL

您可以藉由使用檢測程式碼剖析方法，將程式碼剖析資料的收集限制在應用程式中的一或多個 DLL。 若要對應用程式中的一或多個 DLL 進行分析，請建立包含 .*dll* 檔案作為目標的效能工作階段。 您可以將要進行分析的 DLL 指定成 Visual Studio 方案中的專案，或是指定成獨立的二進位檔案。

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>限制檢測 Visual Studio 方案中的特定 DLL

1. 在 Visual Studio 中開啟包含該 DLL 的方案。

2. 選取 [分析] 功能表上的 [啟動效能精靈]。

3. 選擇 [檢測] 做為程式碼剖析方法，然後按 [下一步]。

4. 從 [您要對下列哪一項可用目標進行分析？]，選取 .*dll* 專案的名稱，然後按一下 [下一步]。

5. 按一下 [完成] 結束精靈，並將新的效能工作階段顯示在 [效能總管] 視窗中。

6. 以滑鼠右鍵按一下 [目標]，然後選取 [加入目標專案]。

7. 從 [加入目標專案] 清單中，選取您要用來執行 DLL 的可執行專案。

     選擇性。 您可以加入要進行程式碼剖析的其他任何 DLL 專案。

8. 如果不要對某個已加入的專案收集資料，請以滑鼠右鍵按一下該專案的名稱，然後再清除 [檢測] 核取方塊。

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>將要進行程式碼剖析的特定 DLL 指定成獨立的二進位檔

1. 開啟 Visual Studio。

2. 選取 [分析] 功能表上的 [啟動效能精靈]。

3. 從 [您要對下列哪一項可用目標進行程式碼剖析]，選取 [為動態連結程式庫 (.DLL) 進行程式碼剖析]，然後按 [下一步]。

4. 在精靈的第二頁執行下列步驟：

    - 在 [DLL 路徑] 中，鍵入要進行分析之 .*dll* 檔案的路徑和檔名。 您也可以按一下省略符號按鈕 (...)，在 [要進行程式碼剖析的動態連結程式庫] 對話方塊中尋找檔案。 請注意，您必須指定接下來選取之可執行檔 (.*exe*) 所啟動的 .*dll* 檔案複本。

    - 在 [可執行檔路徑] 中，鍵入要執行 .*dll* 之可執行檔 (.*exe*) 的路徑和檔名。 您也可以按一下省略符號按鈕 (...)，在 [要啟動的可執行檔] 對話方塊中尋找檔案。

    - 選擇性。 在 [命令列的引數] 中，輸入要傳給可執行檔的任何命令列引數。 如有必要，請在 [工作目錄] 中指定應用程式的工作目錄。

    - 按 [ **下一步**]。

5. 選擇 [檢測] 做為程式碼剖析方法，然後按 [下一步]。

6. 按一下 [完成] 結束精靈，並將新的效能工作階段顯示在 [效能總管] 視窗中。

7. 選擇性。 若要新增其他 .*dll* 檔案，請以滑鼠右鍵按一下 [目標]，然後選取 [新增目標二進位檔]。 接著再從 [加入目標二進位檔] 對話方塊選取檔案。

    > [!NOTE]
    > 請勿指定執行 DLL 的可執行檔 (.*exe*)。

## <a name="see-also"></a>另請參閱

[控制資料收集](../profiling/controlling-data-collection.md)
[如何：限制檢測特定函式](../profiling/how-to-limit-instrumentation-to-specific-functions.md)