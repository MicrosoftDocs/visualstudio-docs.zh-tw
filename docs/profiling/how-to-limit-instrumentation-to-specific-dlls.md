---
title: 如何：限制檢測特定 DLL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 066262a3fae35e82904b011165813e9dd75d9987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778813"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>如何：限制檢測特定 DLL

您可以藉由使用檢測程式碼剖析方法，將程式碼剖析資料的收集限制在應用程式中的一或多個 DLL。 要分析應用程式中的一個或多個 DLL，請創建一個包含 的性能會話。*dll*檔作為目標。 您可以將要進行分析的 DLL 指定成 Visual Studio 方案中的專案，或是指定成獨立的二進位檔案。

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>限制檢測 Visual Studio 方案中的特定 DLL

1. 在 Visual Studio 中開啟包含該 DLL 的方案。

2. 選取 [分析]**** 功能表上的 [啟動效能精靈]****。

3. 選擇 [檢測]**** 做為程式碼剖析方法，然後按 [下一步]****。

4. 從以下**哪些可用目標中，您要分析哪些目標？***dll*專案，然後按一下 **"下一步**"。

5. 按一下 [完成]**** 結束精靈，並將新的效能工作階段顯示在 [效能總管]**** 視窗中。

6. 以滑鼠右鍵按一下 [目標]****，然後選取 [加入目標專案]****。

7. 從 [加入目標專案]**** 清單中，選取您要用來執行 DLL 的可執行專案。

     選擇性。 您可以加入要進行程式碼剖析的其他任何 DLL 專案。

8. 如果不要對某個已加入的專案收集資料，請以滑鼠右鍵按一下該專案的名稱，然後再清除 [檢測]**** 核取方塊。

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>將要進行程式碼剖析的特定 DLL 指定成獨立的二進位檔

1. 開啟 Visual Studio。

2. 選取 [分析]**** 功能表上的 [啟動效能精靈]****。

3. 從 [您要對下列哪一項可用目標進行程式碼剖析]****，選取 [為動態連結程式庫 (.DLL) 進行程式碼剖析]****，然後按 [下一步]****。

4. 在精靈的第二頁執行下列步驟：

    - 鍵入 的路徑和檔案名。*dll*檔，你想在**Dll 路徑**中設定檔。 您也可以按一下省略符號按鈕 (...)，在 [要進行程式碼剖析的動態連結程式庫]**** 對話方塊中尋找檔案。 請注意，必須指定 的副本。*dll*檔，將由可執行檔啟動 （。*exe*） 檔，您選擇下一個。

    - 鍵入可執行檔的路徑和檔案名 （。*exe）* 檔將行使 。*dll*在**可執行路徑**中。 您也可以按一下省略符號按鈕 (...)，在 [要啟動的可執行檔]**** 對話方塊中尋找檔案。

    - 選擇性。 在 [命令列的引數]**** 中，輸入要傳給可執行檔的任何命令列引數。 如有必要，請在 [工作目錄]**** 中指定應用程式的工作目錄。

    - 按 [下一步]****。

5. 選擇 [檢測]**** 做為程式碼剖析方法，然後按 [下一步]****。

6. 按一下 [完成]**** 結束精靈，並將新的效能工作階段顯示在 [效能總管]**** 視窗中。

7. 選擇性。 添加更多 。*dll*檔，按右鍵**目標**，然後選擇 **"添加目標二進位**檔 "。 接著再從 [加入目標二進位檔]**** 對話方塊選取檔案。

    > [!NOTE]
    > 不要指定可執行檔 （。*exe*） 檔，以執行 DLL。

## <a name="see-also"></a>另請參閱

[控制資料收集](../profiling/controlling-data-collection.md)
[如何：將檢測限制為特定函數](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
